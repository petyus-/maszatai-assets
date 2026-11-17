NEW HOOK VARIANTS (same proven pin logic as mountA_v10_hook):

1. hook_xmas.stl — Christmas star plate (5-point star, prints flat, red-friendly)
   Fits the same 150mm digital caliper; hang = slide slider window over pin.

2. hook_long300.stl — tall plate (140mm) + lower guide peg for 200-300mm calipers
   (long tails swing on a single hook; the peg stops the wobble).

3. rack_triple.stl — 3 hooks on one plate (caliper + micrometer + pencil/tool),
   110x70mm plate.

All: pin 4mm dia, 38mm reach, slider window ride-on, zero-collision verified
logic (same as v10), flat print, no supports. Listing copy: same plain style,
"slide it on, lift it off".

TREE v3 (replaces the smooth-cone tree on the shop):
- star standing VERTICAL on top (real 5-point star, press-fit slot in the top stub)
- stepped 11 tiers with triangle through-windows on the lower 8 discs
- candle cavity under the tree: 42mm dia x 26mm high, open front arch —
  fits an LED tea light; light leaks through the triangle windows
- 98mm tall, prints flat, no supports (star prints inserted; slot prints clean)
- listing copy: "Candle-lit Christmas tree — slide an LED tea light under the
  arch and watch the glow shine through the triangle windows. Star stands
  upright on top. Prints in one piece, no supports."

CABLE CLIP v3 (replaces BOTH old concepts - ring and C-ring):
Normal commercial-style wall clip, human logic: press cable in from the front, done.
- flat back plate (adhesive pad + screw hole) against the wall
- open-top slot on the FRONT face: cable presses in from above, snap bumps grip
- 6.4mm channel + 4mm snap throat for 6mm cable: positive retention, pull to release
- slot floor at 3mm carries the weight; cable runs vertically along the wall
- 16x12x10mm body + flange; prints flat on its back in ~10 min, no supports
- sizes: 6mm (now), 8mm + 10mm = same script, CH_W 8.4/10.4
- listing copy: "Press the cable in from the front - it snaps in and stays.
  Screw or stick the clip to the wall. To remove, pull the cable out.
  That's it. No threading, no rings."

TREE v5 — HANGING ORNAMENT (Peti: "this will be hung on a Christmas tree"):
- side arch CLOSED (light stays inside; sides solid again)
- LED goes in from BELOW: Ø39.5 bottom port, LED tea light (Ø38 body + Ø42 rim)
  flexes past two half-circle snap tabs at the port mouth -> clicks in, stays
  (35.9mm^3 tab grip = positive snap, twist or pull to change battery)
- internal seat web at z8-10 with Ø37.5 hole holds the LED body centered
- hollow chamber + triangle windows unchanged (light shines through)
- bigger star (r24) with Ø3.8 hanging hole through the top arm — hang it on the
  tree with the LED lit
- 102mm tall, prints upside-down flat (port up) — no supports
- listing copy: "A glowing ornament for the Christmas tree: click an LED tea
  light into the bottom port, hang it by the star, and the light shines
  through the little triangle windows. Battery changes in seconds."

TREE v6 — SCATTERED WINDOWS (Peti: "scatter the triangle holes, 4-5 per level,
no same vertical column, a bit of randomness"):
- same sealed hanging design as v5 (bottom LED snap port, star hanging hole)
- 50 triangle windows scattered over 11 tiers, 4-5 per tier
- seeded RNG (seed 42, reproducible): per-hole angle jitter + min 28 deg spacing
  within a tier and min 20 deg vs the tier below (kills vertical columns),
  radial jitter 0-1.5mm, vertical jitter inside each tier wall
- hole size scales with tier radius (8mm at base down to 4mm at top)
- verified: 52/52 raycasts pass through the wall into the cavity
- replaces the v5 window layout in the listing; STL: tree_v6_scatter.stl

TREE v6.1 — WINDOWS FIXED (projected onto the 3D model for real):
Peti approved the scatter map; this build PROJECTS those windows INTO the STL
for real. The previous scatter STL had the cutters landing mostly inside the
wall (blind pockets) — root-caused and rebuilt:
- cutter = point-up triangle prism with RADIAL axis (tangent-z triangle,
  extruded inward 14mm through the 6mm wall) — cannot fail to pierce
- window fully inside its tier band (zc + h <= tier_z + 5.5, no seam crossing)
- verification: radial void probe = 48/49 fully open, 1 apex-sliver borderline
  (tier 10); LED clearance re-checked (38.9mm^3 = tab grip only)
- STL replaced in repo: tree_v6_scatter.stl (this is the real, pierced version)

CUT-THROUGH VIEWS (Peti: show the battery light inside on the listing):
- tree_v6_cutthrough.png: section cut exposing the hollow interior with the
  LED tea light visible in the snap port + light escaping through the windows
- listing gallery order: hanging-glow shot, cut-through (how it works),
  studio front, scatter map
GO-LIVE (Peti approved "make these live"):
- tree listing: swap STL to tree_v6_scatter.stl (v6.1 pierced windows) +
  add cut-through shot to gallery
- cable clip listing: cable_clip_v3_6mm.stl (+ 8mm/10mm variants on request)
  replaces the old ring clips everywhere

LED HOLDER OPTIONS (Peti: "find 2-3 types of supports where the light can be
added and will be kept inside" — the light must be visibly SUPPORTED, nothing
floating; tree hangs, so the holder carries the light's weight):
A — CLICK TABS (tree_led_A_click.stl): bottom Ø39.5 port, LED pushes in from
    below, two half-circle tabs click over the rim flange. Web at z8-10 carries
    the weight. Fastest battery change (2s), no extra parts.
B — SLIDE-IN CRADLE (tree_led_B_slide.stl): sealed bottom; side slot in the
    trunk (44x8mm) with entry lip; light slides sideways onto a cradle web.
    Most "toy-like" to use; sealed base = no light leaks down.
C — TWIST-LOCK BASE (tree_led_C_bayonet.stl + tree_led_C_plate.stl): separate
    Ø39 plate; light rests on the plate's web, plate twists 30° into two
    L-slots (jar-lid logic). Most secure; 2 printed parts.
All three: weight path light->web/ring->wall (nothing floats), star + hanging
hole unchanged, windows unchanged. Peti picks one; that becomes the listing.

ASSEMBLY CLARITY (Peti: "3-part print? or half-split? which is easier?"):
RECOMMENDED = 2-PART KIT (tree_led_A_click.stl + star = same file, star is
molded in): tree prints UPSIDE DOWN flat (port = print bed face, no supports,
no cap part), mini LED puck (Ø38x10) drops into the bottom port, two molded
half-circle tabs click over its rim. Star is the only second part.
- vs Kover's 3-part kit (tree + cap + star): same result, one extra part to
  not lose; only advantage = sealed flat base.
- half-split tree: NOT recommended — visible seam up the whole tree,
  alignment risk, more print area.
4-step assembly diagram: tree_assembly_2part.png

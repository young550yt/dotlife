# ● Dot — a tiny life

One glowing dot on a pitch-black screen. It's a person. It wanders, it
feeds itself, it sleeps — **you're just a spectator.**

## Run it

Double-click **`start.bat`** (or open `index.html` in any browser).
One file, no server, no dependencies.

## What it does (all on its own)

| | |
|---|---|
| **Walk around** | wanders on its own with curved, uneven paths — speeds up, slows down, stops for a breather now and then |
| **Eat** | when hunger builds, a meal appears somewhere on screen — it walks over and eats it bite by bite, no input from you |
| **Sleep** | energy drains while awake — at empty it lies down, glow turns moonlit blue, `z`s drift up, then it wakes recharged |

The current activity is always shown at the **lower-left** of the screen:
`walking around` / `eating` / `sleeping`.

## Why the movement doesn't look robotic

- **Smooth steering, not waypoints** — a capped steering force eases it
  toward a heading, so it curves instead of snapping between points
- **Layered sine "noise"** heading + a side-to-side slalom wobble →
  paths are never straight lines
- **Variable speed** — breathes between ~60–105 px/s, with random
  standing-still pauses (0.4–1.5 s) every few seconds
- **Soft edges** — the screen border gently pushes it back in a curve,
  no bouncing off walls
- **Body language** — squash-and-stretch along travel direction,
  breathing when idle, glow that pulses faster awake and slow/dim asleep

## Details

- Warm candle glow awake → cool blue while sleeping (smooth colour lerp)
- Crumb particles on each bite, soft trail while walking, wake-up ripple
- Self-feeding loop: hunger climbs ~2.3/s → meal spawns at 44 → 3 bites
  drop it back to ~0 → repeat forever
- Food fades after 25 s if ignored; energy drains ~2/s awake, regens ~11/s asleep
- Subtle Web Audio blips on bites/waking (starts on your first click —
  browsers block sound until then; clicking also tosses it an extra treat,
  but it never needs one)
- Activity text fades in on every change

## Files

| File | Role |
|---|---|
| `index.html` | the whole game (~17 KB, self-contained) |
| `start.bat` | opens it |

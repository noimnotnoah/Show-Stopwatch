# Show StopWatch

A single-page web app for timing live performances — built for stage managers who need to track running times, playing times, intervals, and show stops without juggling a stopwatch and a notebook.

No install, no build step, no dependencies to manage. It's one HTML file. Open it in a browser and it works.

## Getting started

1. Open `show-stopwatch.html` in any modern browser (Chrome, Safari, Firefox, Edge).
2. To use it on a phone or tablet, add it to your home screen from the browser's share/menu so it opens full-screen like an app.
3. That's it — no server, no account, no internet connection required after the page loads.

## How it works

**1. Set the Show**
Build tonight's running order. Add as many acts and intervals as the show needs, in any order, and rename them (e.g. "Act 1", "Panto Interval", "Act 2"). Intervals get a planned length in minutes. Reorder rows with the ↑ / ↓ buttons, or remove one with ✕.

**2. Pre-Show**
Tap **Mark now** to log House Open and Clearance times, then tap **Begin Act 1** to bring the show up.

**3. Running a show**
- The big number in the middle is the live clock: white and counting up during an act, green and counting down during an interval (it turns red and counts up if the interval overruns).
- **+ Start a Timer** logs as many named in-act timers as you like (scenes, effects, whatever needs tracking) — stop each one independently.
- **Show Stop** (top-right, red) pauses the clock and records the stop separately, so playing time stays accurate. Tap it again to resume.
- **Interval Safe Mode** locks the "end interval" action behind an extra unlock tap, so you can leave the screen on and in view without risking an accidental tap forward.
- **Show Times** opens a running summary at any point — running time, playing time, interval time, show-stop time, and a breakdown by act/interval.
- The amber button at the bottom always tells you exactly what happens next (e.g. "End Act 1 & Start Interval") and advances the show.

**4. Show Complete**
Once the last act ends, you get a full report: all totals plus a per-act/interval breakdown. Copy it, share it (on supported devices/browsers), or save it and start a new show.

**5. Previous performances**
Saved reports are kept in the browser's local storage so you can look back at past shows. Tap any entry to see its report.

## What it calculates

- **Running time** — from Clearance (or House Open, or the first act if neither was logged) to the end of the show.
- **Playing time** — total time across all acts, excluding show stops.
- **Interval time** — total time across all intervals, excluding show stops.
- **Show stop time** — total time the show was stopped, tracked separately and subtracted from playing/interval time.

## Good to know

- **Local storage only.** Show history lives in the browser you're using — it won't sync between your phone and laptop, and clearing browser data will clear it too.
- **No push notifications.** Because this is a web page rather than a native app, it can't send background alerts (e.g. a "Beginners call" ping) if you switch apps or lock your phone. The in-app call countdown only updates while the page is open and visible.
- **Keep the screen on.** Most phones will dim or sleep the screen after inactivity. There's no way for a web page to fully override that — Interval Safe Mode helps you leave it open safely, but for a phone that sleeps aggressively, adjust your device's auto-lock setting during a show.
- **One file, no build tools.** Everything — HTML, CSS, and JavaScript — lives in `show-stopwatch.html`. Open it directly; there's nothing to compile or install.

## Customizing

Everything is in that one file, so it's easy to tweak by hand:
- **Call timing** — the "Five" and "Beginners" call offsets are set near the top of the `<script>` block (`fiveOffsetMin`, `beginnersOffsetMin`), in minutes before the end of an interval.
- **Rounding** — set `rounding` to `1` or `5` to round all logged times to the nearest 1 or 5 minutes; `0` turns rounding off.
- **Colors and fonts** — all defined as CSS variables at the top of the `<style>` block (`--bg`, `--green`, `--amber`, etc.), so a palette or font swap is a find-and-replace away.

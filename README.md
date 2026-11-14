# Dynamic Island for Windows 11 (Windhawk mod)

An interactive, fluid **Dynamic Island** overlay and taskbar companion for Windows 11, built as a [Windhawk](https://windhawk.net/) mod. Brings smooth Apple-inspired micro-interactions, live status pills and HUD alerts to the desktop.

![platform](https://img.shields.io/badge/platform-Windows%2011-blue) ![license](https://img.shields.io/badge/license-MIT-green)

## Features

- **Adaptive taskbar placement**
  - Top taskbar: embeds into the taskbar and expands downward.
  - Bottom / left / right taskbar: floats as an independent pill with spring animations.
- **Live activities (persistent & expandable)**
  - **Now Playing**: album artwork (media session → **iTunes Search API** fallback → placeholder gradient), marquee track/artist info, animated equalizer with per-frame smoothed bars, expanded playback controls, interactive seek bar.
  - **Focus Timer**: circular progress, MM:SS countdown, pause/resume/stop controls.
  - **Microphone privacy dot**: shows when an app is accessing the microphone.
- **Transient HUD alerts (auto-dismissing)**
  - Volume changes, Caps Lock / Num Lock toggles, charger plug/unplug, low battery, Bluetooth device connection (with battery level when reported).
- **Fluid spring physics** — `cubic-bezier(0.34, 1.3, 0.5, 1)` motion, compact ⇄ expanded morphing.
- **Hardware-accelerated rendering** — Direct2D + DirectWrite, layered window, ~30 FPS when active.
- **Tunable** — font family/weight/size, HUD toggles, idle visibility, media visibility policy, animation and debug hotkeys (Ctrl+Win+1..9, 0).

## Installation

1. Install [Windhawk](https://windhawk.net/).
2. Open Windhawk → **Create a new mod** (or "Explore" → new mod editor).
3. Replace the template with the contents of [`win11-dynamic-island.wh.cpp`](win11-dynamic-island.wh.cpp).
4. **Compile** and enable the mod.
5. Open **Settings** in the mod editor to customize behavior.

## Requirements

- Windows 10 (1809+) / Windows 11.
- Media controls use the Windows media session API (GSMTC); album art falls back to the iTunes Search API when the media session provides none.

## Building manually

The mod is compiled by Windhawk itself (bundled LLVM/MinGW, C++23). For a standalone syntax check:

```
clang++ -fsyntax-only -std=c++23 -target x86_64-w64-mingw32 \
  -DUNICODE -D_UNICODE -D_WIN32_WINNT=0x0A00 -DWH_MOD \
  -include windhawk_api.h win11-dynamic-island.wh.cpp
```

## Credits

- Inspired by [devcode90/Dynamic-Island-for-Windows](https://github.com/devcode90/Dynamic-Island-for-Windows).
- Authors: **Tederby** and **Qhaton**.

## License

[MIT](LICENSE)

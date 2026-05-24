# Aristo Music Player Pro

> v1.0 · Single-file HTML App · No dependencies · Works 100% offline

---

## Overview

SONIQ is a fully self-contained, offline music player delivered as a single HTML file. There is nothing to install, no server required, and no data leaves your device. Open it in any modern browser, load your audio files, and enjoy a full-featured playback experience with real-time audio visualization, speed control, and a sound filter system accessible directly from the keyboard.

---

## Features

### Playback
- Play, pause, skip to next or previous track
- Seek by clicking anywhere on the progress bar
- Persistent queue — tracks stay loaded between plays
- Auto-advance to the next track when a song ends

### Visualizer
- Real-time frequency spectrum analyser using the Web Audio API
- Animated background particle field that reacts to the bass beat
- Color hue cycles continuously so visuals never look static
- Idle animation keeps visuals alive even before a file is loaded

### Speed Control
- Slider range: 0.50× to 2.00× in 0.05 steps
- Playback rate changes apply immediately without reloading the track
- Speed is preserved when switching between tracks in the playlist

### K Sound Filter
- Press `K` to cycle through four distinct audio effects in sequence
- Each press advances to the next filter; the effect name appears on screen
- Filters are powered by Web Audio BiquadFilter and WaveShaper nodes

---

## K Filter Reference

Each press of `K` cycles to the next filter. Pressing `K` on the last filter loops back to the first.

| Filter | Type | Description |
|--------|------|-------------|
| ⚡ LASER | Bandpass @ 2kHz | Isolates the mid-punch frequencies for a slicing, laser-like tone |
| 🌊 DEEP SUB | Lowpass @ 120Hz | Strips everything except the sub-bass and low rumble |
| 🔥 CRUNCH | Highpass @ 3kHz + distortion | Adds harmonic grit and presence via waveshaper |
| ✨ AIR | Peaking EQ @ 12kHz +12dB | Adds brightness and shimmering high-end air |

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Toggle play / pause |
| `K` | Activate or cycle through sound filters |
| `← Arrow` | Seek back 5 seconds |
| `→ Arrow` | Seek forward 5 seconds |

---

## Getting Started

**1. Open the file**
Double-click `music-player.html` or drag it into any browser tab. No web server needed.

**2. Add audio files**
Click the `+ ADD` button to pick one or more audio files from your device. Supported formats: MP3, AAC, FLAC, OGG, WAV, OPUS.

**3. Press Play**
The first file loads automatically. Use the controls, keyboard shortcuts, or the playlist to navigate.

**4. Explore the filters**
Press `K` at any time to switch to the next sound filter. The effect activates instantly on the live audio. The filter name appears as a badge on the visualizer panel and as a brief toast notification.

---

## Browser Support

| Browser | Minimum Version | Notes |
|---------|----------------|-------|
| Chrome / Edge | 66+ | Full support |
| Firefox | 76+ | Full support |
| Safari | 14.1+ | Full support; use HTTPS or local file |
| Opera | 53+ | Full support |

---

## Technical Notes

- All audio processing is done via the browser's built-in Web Audio API — no external library is used
- AudioContext is created lazily on first user interaction to comply with autoplay policies
- Object URLs created for uploaded files are not revoked during the session so tracks can be re-loaded
- The visualiser runs at the browser's native frame rate via `requestAnimationFrame`
- Speed control uses the `HTMLMediaElement.playbackRate` property — pitch is preserved in most browsers
- Distortion in the CRUNCH filter uses a tanh-style waveshaper curve with 4× oversampling

---

## File Structure

The entire application is one file:

```
music-player.html
```

HTML structure, CSS styles, and JavaScript logic are all embedded inline. The only external resources are two Google Fonts (Space Mono and Syne) loaded for typography — these fall back gracefully when offline.

---

*Aristo Music Player Pro · Built with Web Audio API · No rights reserved*

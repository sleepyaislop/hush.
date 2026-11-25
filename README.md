# Hush 0.2 — Android-friendly adaptive masking prototype

This is a Progressive Web App (PWA). It runs in Chrome on Android and can be added to the home screen. It is not yet a native Android APK.

## Files
- `index.html` — interface, microphone analysis, noise generator and masking controls
- `manifest.webmanifest` — installable app metadata
- `sw.js` — basic offline caching

## Run it
Microphone access requires HTTPS (or localhost). Do not open `index.html` directly from a file manager.

A beginner-friendly publishing route:
1. On your phone, create a GitHub account if you do not already have one.
2. In Chrome, open GitHub and create a new **public** repository named `hush`.
3. Use **Add file → Upload files** and upload all three files, keeping them at the repository root.
4. Open repository **Settings → Pages**.
5. Under Build and deployment, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
6. Wait for GitHub Pages to publish. Open the Pages URL shown there in Chrome.
7. In Chrome's menu, choose **Add to Home screen** or **Install app**.

GitHub Pages makes the source code public. This prototype contains no personal data or secrets. If you prefer not to publish the code, use a private HTTPS static host instead.

## First test
1. Connect headphones before starting Hush.
2. Put the phone near the fridge, microphone unobstructed.
3. Open Hush and grant microphone permission.
4. Start at 5–10% output. Keep headphone volume low.
5. Try Automatic mode while the fridge is running, then try Manual mode.

## Important limitations
- Keep the page open and screen awake during use.
- Browser/device audio routing and Bluetooth latency vary.
- The microphone analyser is intended to observe ambient sound. Headphones reduce, but do not guarantee elimination of, feedback from the generated sound.
- The current automatic algorithm follows the strongest local peak in 40 Hz–1 kHz. It cannot reliably distinguish the fridge from speech, traffic or other sources.
- The noise is masking, not destructive-interference cancellation. It does not guarantee that the fridge will become inaudible.
- The output level is deliberately capped in the UI, but always begin quietly and stop if uncomfortable.
- This prototype processes audio locally and does not record or upload microphone audio.

## Next engineering improvements
- Better persistent-peak tracking and fridge-onset detection.
- Adjustable target band and notch/peak visualisation.
- Better pink/brown noise calibration and output loudness control.
- Explicit headphone route check and screen-wake support.
- Native Android version using Kotlin and a low-latency audio engine.

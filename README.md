# Spatial Playground

A React + Vite + PWA learning demo for 3D viewing and cross-platform AR launch.

## Features
- 3 sample 3D models (loaded from modelviewer.dev sample assets)
- 3D orbit/zoom controls
- AR launch using `model-viewer` modes: WebXR, Android Scene Viewer, iOS Quick Look
- Scale control, auto-rotation toggle, floor/wall placement selection, preview themes
- Responsive Persian RTL UI
- PWA manifest and app-shell service worker

## Requirements
- Node.js 20+
- HTTPS for device camera / WebXR / AR launch (localhost is allowed for local development)
- Android: ARCore-certified device and Google Play Services for AR for native AR experiences
- iPhone/iPad: Safari for AR Quick Look; model must be available as USDZ or converted by model-viewer

## Run locally
```bash
npm install
npm run dev
```

Open the local network URL on a phone on the same Wi-Fi for the 3D preview. For actual AR on a phone, deploy to an HTTPS host (for example Cloudflare Pages or Netlify).

## Build
```bash
npm run build
npm run preview
```

## Important limitations
- The 3D sample models are fetched from modelviewer.dev, so the first load needs internet.
- The service worker caches the app shell only; it does not cache the external 3D models or native AR runtime.
- On iOS, the AR button opens Apple's AR Quick Look. The webpage cannot keep controlling the model while Quick Look is open.
- On Android, the component prefers WebXR where supported, then Scene Viewer, then Quick Look.
- The floor/wall setting is passed to the AR viewer; exact placement behavior depends on the platform's native AR viewer.
- This is a classroom prototype, not a full custom SLAM / persistent shared-anchor implementation.

## Suggested next upgrades
1. Add local GLB + USDZ assets for offline use.
2. Add a custom WebXR hit-test flow for Android with reticle-based placement.
3. Add ARKit / RealityKit native iOS build if custom persistent anchors are required.
4. Add QR-based shared experiences and backend persistence.

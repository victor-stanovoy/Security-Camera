# SecureCam

A single-page security camera system built on [LiveKit](https://livekit.io). No backend and no build step: one `index.html`.

- Several cameras and inputs from one device (all webcams, phone front/back, screen capture, microphone)
- Watch every camera from a phone or another computer
- Watermarks burned into the video (text, camera name, timestamp, tiled)
- Low-profile mode (black screen or plain document, neutral tab title)
- Shows local and public IP address
- Cameras restart automatically after a reload or a dropped connection

## Deploy on GitHub Pages

1. Create a repository (for example `securecam`) and upload `index.html` to the root.
2. Go to **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
3. After a minute the app is live at `https://<your-username>.github.io/securecam/`.

Pages serves the app over https, which browsers require for camera access and for signing tokens.

## First-time setup

1. Create a free project at [cloud.livekit.io](https://cloud.livekit.io), then create an API key under **Settings → Keys**.
2. Open the app, go to **Setup**, and enter the WebSocket URL (`wss://…`), room name, API key and secret.
3. Press **Save & test connection**.

## Using it

- **Camera device (laptop):** Camera tab → Detect cameras → tick inputs → Start selected. Tick "Restart these cameras automatically" for an always-on setup, then use Low-profile mode.
- **Viewer (phone):** On the laptop, Setup tab → set the app address → Viewer link, then scan the QR code or open the link on the phone. It connects and shows all cameras.
- **Phone as a camera too:** use "Full device link" and open it on your own phone.

## Security notes

- Your API key and secret are entered in the page and stored only in that browser's localStorage. Never commit them to the repository.
- The viewer link contains a view-only token valid for 30 days. The full device link contains your API secret: use it only for your own devices.
- To revoke viewer links, rotate the API key in LiveKit.
- Only point cameras at places where everyone present knows about them. Covert recording of people is illegal in many countries.

## Known limits

- Browsers show a camera-in-use indicator that the app cannot and should not hide.
- Browsers throttle pages that are in the background or sleeping. Keep the camera tab open, and keep a phone's screen on and plugged in.
- iPhones are better as viewers than as cameras: Safari limits background capture. Android with Chrome works well as a camera.

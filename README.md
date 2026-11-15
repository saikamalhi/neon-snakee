# NEON SNAKE — Flask Arcade Website

A from-scratch browser Snake game with a Flask-powered website shell, responsive neon arcade UI, keyboard/touch controls, increasing difficulty, and locally saved high score.

## Requirements
- Python 3.8 or newer
- pip
- A modern browser (Chrome, Firefox, Edge, Safari)

## Run on Windows
1. Extract `neon-snake.zip`.
2. Open the extracted `neon-snake` folder.
3. In the address bar of File Explorer type `cmd` and press Enter.
4. Create and activate a virtual environment (recommended):
   ```bat
   py -m venv venv
   venv\Scripts\activate
   ```
5. Install Flask:
   ```bat
   py -m pip install -r requirements.txt
   ```
6. Start the website:
   ```bat
   py app.py
   ```
7. Open **http://127.0.0.1:5000** in your browser. Keep the terminal open while playing.

If `py` is unavailable, try `python` in its place.

## Controls
- Arrow keys or W/A/S/D: steer
- Space: pause/resume
- On phones/tablets: tap the on-screen directional pad or swipe on the board
- Start Game, Pause/Resume, and Restart buttons are available below the board

## Game rules
Collect the pink energy diamond for 10 points and grow the snake. The game gets faster every 50 points. Hitting a wall or the snake's body ends the run. Your best score is stored in this browser's localStorage; it is local to that browser/device and can be cleared with browser site data.

## Project structure
```text
neon-snake/
├── app.py
├── requirements.txt
├── README.md
├── templates/
│   └── index.html
└── static/
    ├── css/style.css
    ├── js/game.js
    └── images/          (reserved for optional local artwork)
```

## Customization
- Branding, sections and page structure: `templates/index.html`
- Colors, layout and responsive styles: `static/css/style.css` (`:root` variables at the top)
- Game rules, speed curve, controls and rendering: `static/js/game.js`
- Flask routes: `app.py`

Google Fonts are loaded from Google Fonts when internet is available. If offline, the site uses the listed local system fallbacks. The game itself does not require any paid service or external game host.

## Deploy online
For a simple public deployment, use a Python host such as Render or PythonAnywhere:
1. Create an account and upload this project to a Git repository (or the host's supported upload flow).
2. Set the build/install command to `pip install -r requirements.txt`.
3. Use a production WSGI server such as Gunicorn on Linux hosts: add `gunicorn` to `requirements.txt`, then set the start command to `gunicorn app:app`.
4. Configure the host's Python web service to expose its assigned public URL.

Do not use Flask's `debug=True` development server as the public production server. For PythonAnywhere, configure a Flask web app and point its WSGI file to this project's `app` object. Deployment provider dashboards and free-tier availability can change; check the provider's current instructions. Your source code remains yours and can be moved to another host.

## Notes
- Flask serves the page and the `/health` endpoint. Real-time game logic runs in JavaScript in the visitor's browser for responsive controls.
- High scores are not uploaded to the Flask server; they remain in browser storage.
- The `static/images/` directory is intentionally included for future assets; no external game assets are required.

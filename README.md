One-Time Secret — Pure PHP (No DB)
=====================================

What it is
---------
A small Privnote-style app written in pure PHP that stores secret messages as encrypted JSON files in a local `secrets/` folder.
Each secret can be protected with a password and set to expire after a chosen time. When a secret is read once it is destroyed immediately.

How to run on KSWeb / Local server
----------------------------------
1. Copy the `one-time-secret` folder into your KSWeb www folder (or XAMPP htdocs).
2. Make sure the `secrets/` folder is writable by the server.
3. Open your server URL, e.g. `http://localhost/one-time-secret/` or the local IP your Android serves.
4. Create a secret and open the generated link once to view and destroy it.

Security notes
--------------
- The app uses a server-side constant `ENC_KEY` in `helper.php` for AES-256-CBC at-rest encryption. Change it to a long random string before using on any public-facing server.
- `.htaccess` is included to block direct web access to files in `secrets/` (if using Apache-compatible server).
- Passwords are hashed using PHP's `password_hash()` and verified with `password_verify()`.
- This project is intended as a simple demo. For production, consider stronger key management and HTTPS.

Files included
--------------
- index.php — form to create secrets
- process_secret.php — handles creation and returns link
- read.php — view and destroy secret (handles password flow)
- helper.php — core utilities and encryption
- delete_old.php — simple cleanup script to remove expired secrets
- assets/ — CSS and JS for a modern responsive UI
- secrets/ — storage (must be writable)
- README.md — this file

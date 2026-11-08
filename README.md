# Rk Editing portfolio

A responsive portfolio for an independent video editor and photographer, with a separate Firebase-backed content manager.

## Run it

Serve this folder over HTTP to use the ES module scripts and Firebase CDN SDK. For example, run `python3 -m http.server 8000` from this folder, then open `http://localhost:8000/` for the portfolio and `/admin.html` for the content manager. No project build step is required.

The styles are split across `styles.css` and `admin.css`; the site and editor behavior live in `app.js` and `admin.js`. Firebase app configuration, Authentication, and Firestore instances are exported from `firebase-config.js`. Profile data is stored in `settings/profile` and projects in the `projects` collection. Project documents include a server-generated `timestamp`; the public page listens for project changes with Firestore `onSnapshot` and reads at most 100 projects. The admin initializes demo content once in a new Firestore database after an authenticated admin signs in. Cover images are referenced by URL; their URLs are saved in Firestore. The public page uses the local stylesheet without the Tailwind CDN.

Before deploying, configure Firestore rules to allow writes only to authenticated users and reads according to your publishing needs. The admin uses Firebase Email/Password Authentication. Client-side Firebase configuration is public; protect data with security rules.

## Add your own work

In the admin page, sign in with an authorized Firebase Email/Password account. Edit your display name, email, phone, location, Instagram username, WhatsApp number, and bio. The home hero photo URL and the About section headline, copy, service list, image URL, image description, and caption are also customizable. Instagram and WhatsApp links are shown in the public contact section when valid values are set. Add or edit projects with an online cover image URL and, for video projects, an optional YouTube link or MP4 URL. YouTube watch, short, and youtu.be links open in an embedded player. Use the project filters and select a project on the public page to preview its image or video.

The included project content and contact information are demo placeholders. Replace them with the client's real details, photography, and video links before publishing. The demo video links and portfolio imagery require an internet connection.

## Publishing

Edits are shared through Firestore rather than browser storage. The admin requires sign-in; keep admin accounts restricted to trusted editors and review Firestore rules before publishing. The contact links open the visitor's email or phone app.

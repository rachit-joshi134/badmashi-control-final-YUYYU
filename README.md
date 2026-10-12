# NextLayer Studio + ISRO Racing — Netlify-ready project

## What's included
- `public/index.html`: NextLayer Studio hub with AI and RACING divisions, AI service catalogue (voice engineering, AI editing, websites, automation, custom software) and a quote-request form that opens a prefilled email draft.
- `public/isro/index.html`: ISRO motorsport site in black / white / racing red style, public driver directory, leaderboard, registration and driver/certificate reference verification.
- `netlify/functions`: serverless API functions for public drivers, verification, registration, admin login and admin management.
- Netlify Blobs provides persistent JSON storage for this starter backend. Admin dashboard supports driver creation/edit/status/star designation/deletion, certificate create/edit/status/deletion, registration review and audit log.
- `netlify.toml`: Netlify build, function and route configuration.

## Deploy correctly (not just drag-and-drop)
This package contains Netlify Functions, so deploy the **whole folder/repository through Git-connected Netlify or Netlify CLI**. A plain static drag-and-drop upload will not reliably build/deploy the backend functions.

### Recommended
1. Extract the ZIP.
2. Install Node.js 20+.
3. Open terminal in this folder:
   ```bash
   npm install
   npx netlify login
   npx netlify init
   ```
4. Create an admin password hash:
   ```bash
   node -e "require('bcryptjs').hash(process.argv[1],12).then(console.log)" "YOUR-LONG-ADMIN-PASSWORD"
   ```
5. In Netlify Site configuration → Environment variables, set:
   - `ADMIN_EMAIL`
   - `ADMIN_PASSWORD_HASH` (the bcrypt output, not the plain password)
   - `JWT_SECRET` (long random secret, 32+ characters)
6. Run locally with `npx netlify dev`, or deploy:
   ```bash
   npx netlify deploy --prod
   ```
7. Open `/` for NextLayer Studio and `/isro/` for ISRO.

## Important integration note
No original NextLayer Studio source files were provided in this chat, so this ZIP is a Netlify-ready integration starter that preserves an AI division entry point and adds a RACING division. It cannot magically merge your unseen existing AI application code. To preserve every existing feature exactly, the original NextLayer project folder must be merged with these files rather than overwritten.

## AI quote form
The quote form is front-end only and prepares a message for `hello@nextlayer.studio` in the visitor's default email application. It does not silently upload form data or guarantee delivery. Change this destination in `public/index.html` if your preferred business inbox is different.

## Demo content
Driver profiles and points are illustrative starter records. Replace with authorized real data before public launch. Public endpoints never expose medical/identity records. This starter does not collect medical details or document uploads.

## Backend notes
The API uses Netlify Functions and Netlify Blobs. Configure environment variables and deploy the site via Netlify build/CLI/Git. For high-volume or highly sensitive production use, consider a managed database with access controls, backups and reviewed privacy/security policies.

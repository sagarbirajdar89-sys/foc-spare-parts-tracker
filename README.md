# FOC Spare Parts Tracker

## Included
- Mobile-friendly web app, installable as a PWA when hosted over HTTPS.
- IndexedDB local persistence in the browser.
- Loan register, dealer ledger, ageing, company FOC supply and dealer receipt tracking.
- Partial quantity settlement: record each new company FOC supply, dealer receipt and unused return separately; cumulative outstanding recalculates automatically.
- Settlement history log with date and reference for each partial entry.
- CSV exports (opens in Excel), print / Save as PDF, JSON backup and restore.
- Offline shell caching after first load.

## Run locally
Open `index.html` in a modern browser. For PWA install/offline service worker, serve the folder over HTTPS (or localhost).

Example with Python installed:
`python -m http.server 8000`
Then open `http://localhost:8000`.

## Android
Host the folder on an HTTPS website, open it in Chrome on Android, then use the browser menu > Install app / Add to Home screen (or the app's Install button if offered).

## Important storage limitation
This edition stores records in the browser's IndexedDB on that device/browser profile. It is persistent across normal restarts, but clearing browser data or losing the device can remove it. Use Download full backup (JSON) regularly. It does not sync between Android and Windows. Multi-device sync, login and managed cloud backups require a hosted backend/database and authentication.

## Settlement logic
Outstanding = borrowed quantity - dealer received quantity - unused quantity returned.
Company FOC supplied quantity is tracked separately and dealer received quantity cannot exceed company supplied quantity.
A loan closes when outstanding reaches zero.

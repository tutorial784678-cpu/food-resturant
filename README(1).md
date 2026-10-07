# BiteRush + Premier PayFast

A responsive fast-food restaurant website with:
- `index.html` customer ordering page
- `admin.html` admin dashboard
- `server.js` Express backend for orders and PayFast API calls
- `package.json` and `.env.example`

## Run

1. Install Node.js 18+.
2. Open this folder in a terminal.
3. Run:
   `npm install`
4. Copy `.env.example` to `.env`.
5. Set `ADMIN_PASSWORD`.
6. Set the real Premier PayFast values:
   - `PAYFAST_API_BASE_URL`
   - `PAYFAST_MERCHANT_ID`
   - `PAYFAST_SECURED_KEY`
   - `PAYFAST_HASH_SECRET` if Premier PayFast issued a separate hash key.
7. Run:
   `npm start`
8. Open:
   `http://localhost:3000`
   and admin at:
   `http://localhost:3000/admin.html`

## PayFast note

The public Premier PayFast developer docs describe a server-side credential flow, tokenized transaction endpoint, tokenized charge endpoint, transaction status endpoint, 3-D Secure handling and HMAC-SHA256 `secured_hash` values. The example implementation follows those documented endpoint names.

Before production, confirm with Premier PayFast:
- the exact production API base URL for your merchant account;
- your merchant's `account_type` / instrument configuration;
- the exact hash field order expected by your onboarding contract;
- the approved hosted/3-D Secure callback domain;
- webhook signing/verification details for your account.

Never put `PAYFAST_SECURED_KEY`, HMAC secrets or the admin password inside `index.html` or `admin.html`.

## Data

Orders are stored in `data/orders.json`. The demo menu/restaurant settings are stored in browser localStorage so you can edit them instantly from the admin panel on the same browser/origin.

For a multi-device production CMS, move the menu/settings into a database.

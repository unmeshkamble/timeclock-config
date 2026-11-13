# timeClock-config

This repository holds the authorised phone numbers for TimeClock. The app reads them during admin setup and when an admin approves a sensitive action. Codes are sent only to these numbers.

Live file: https://unmeshkamble.github.io/timeclock-config/config.json

**Do not edit `config.json` or `config.sig` by hand.** They must be created by the signing workflow, or the app will reject them.

---

## When to change a number

- HR person changes or resigns
- Backup person changes
- A number is entered wrongly

---

## How to change a number (about 3 minutes)

1. Open this repository on GitHub: `https://github.com/unmeshkamble/timeclock-config`
2. Click the **Actions** tab.
3. In the left list, click **Sign config**.
4. Click **Run workflow** (on the right, above the list of runs).
5. Fill in the three boxes:
   - **Config version:** the current version plus 1. The current version is shown in `config.json` on the live file link above. Example: if it says `2`, enter `3`.
   - **HR mobile:** the full number with +91 and 10 digits, e.g. `+919029090321`
   - **Backup mobile:** the full number with +91 and 10 digits, e.g. `+919619615880`
6. Click the green **Run workflow** button.
7. Wait until the run shows a green tick. This takes about one minute.
8. Open the live file link and check that the version and numbers are correct. GitHub Pages can take 1 to 2 minutes to update.

**If only one number has changed, enter the other one unchanged.** The workflow always writes both numbers.

---

## Rules

- **The version must always go up.** Phones reject any version lower than the one they already hold. A lower or repeated version will not reach the phones.
- **Numbers must start with +91 and have exactly 10 digits after it.** The workflow refuses anything else.
- **Never share the signing key.** It is stored as the secret `SIGNING_KEY` in this repository's settings. Do not paste it anywhere else.

---

## If the workflow fails

- **"HR number must be +91 followed by 10 digits"** (or the backup equivalent): check the number has no spaces or missing digits, then run it again.
- **"SIGNING_KEY secret is missing":** the secret was deleted or renamed. Ask the developer to restore it. Do not create a new key without telling the developer, because every phone would reject the new signatures.
- **"Version must be a whole number":** enter digits only, e.g. `3`.

---

## When phones pick up the change

- A phone gets the new numbers when an admin runs **Setup** or a sensitive action, provided the phone has mobile data.
- Automatic daily refresh on all phones is planned but not yet built. Until then, a phone that is never set up or used by an admin keeps the old numbers.
- A phone that is offline keeps using its last saved copy.

---

## Files in this repository

| File | Purpose |
|---|---|
| `config.json` | The HR number, backup number and version. Written by the workflow only. |
| `config.sig` | The signature that proves `config.json` is genuine. Written by the workflow only. |
| `.github/workflows/sign-config.yml` | The workflow that creates and signs the two files above. |
| `README.md` | This file. |

---

## Change history

Add a row each time a number changes.

| Version | Date | HR number | Backup number | Reason |
|---|---|---|---|---|
| 2 | 13 Nov 2026 | +919029090321 | +919619615880 | First signed config |

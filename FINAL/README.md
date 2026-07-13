# SSS College Website — Student Portal with Real Backend

This is your full college website with a real, working backend database for student
attendance, exam marks, fees, and remarks. Students log in with Register Number + Date
of Birth. Staff can update everything live through the **Staff Portal** in the website —
no coding required after this one-time setup.

## ✅ What you need before starting

- **Node.js version 22.5 or newer.** Check by opening a terminal/command prompt and typing:
  ```
  node -v
  ```
  If it says anything below `v22.5.0`, download the latest version from https://nodejs.org
  (choose the LTS version) and install it, then restart your terminal.

## 🚀 First-time setup (only do this once)

1. Open a terminal / command prompt in this folder (the one containing `server.js`).
2. Run:
   ```
   npm install
   ```
   This downloads the one small piece this project needs (Express). It needs internet
   access and will take under a minute.
3. Run:
   ```
   npm start
   ```
4. You'll see:
   ```
   SSS College Student Portal is running
   Open this in your browser:
   http://localhost:3000

   Staff PIN: sss2026
   ```
5. Open that link (`http://localhost:3000`) in your web browser. That's your website —
   fully working, with a real database behind it.

## 👩‍🎓 Student login (for testing)

Three sample students are created automatically the first time you run it:

| Register Number | Date of Birth | Name |
|---|---|---|
| SSS2024001 | 15/08/2006 | Karthik R |
| SSS2024002 | 22/11/2005 | Priya S |
| SSS2024003 | 03/02/2004 | Arun M |

Go to **Student Login** on the website and try logging in with any of these.

## 🔐 Staff Portal (updating student data daily)

1. Click **Staff Portal** in the website's navigation menu.
2. Enter the staff PIN: **sss2026**
3. Select or search for a student by Register Number.
4. Update their attendance, marks, fees, or add a remark — click Save.
5. Changes are saved instantly to the real database. The student will see the new
   data the next time they log in (or refresh the portal page).

**To change the staff PIN:** before running `npm start`, set an environment variable.
- On Mac/Linux: `STAFF_PIN=yourNewPin npm start`
- On Windows (PowerShell): `$env:STAFF_PIN="yourNewPin"; npm start`

## ➕ Adding a brand new student

Right now, new students are added via the API directly (a simple Staff Portal "Add
Student" button can be added later if you'd like — just ask). For now, you can add one
by running this in a second terminal window while the server is running:

```
curl -X POST http://localhost:3000/api/admin/students ^
  -H "X-Staff-Pin: sss2026" -H "Content-Type: application/json" ^
  -d "{\"registerNo\":\"SSS2024004\",\"dob\":\"10/05/2006\",\"name\":\"New Student Name\",\"course\":\"B.Sc Computer Science\",\"semester\":\"I\",\"year\":\"2026-27\"}"
```//
(On Mac/Linux, replace the `^` line-continuation with `\` and remove the `//`.)

Then go to Staff Portal, search for that Register Number, and fill in their attendance,
marks, and fees normally.

## 🛑 Stopping the server

Press `Ctrl + C` in the terminal where it's running.

## 📦 Your data

All student data lives in a file called `students.db` that appears in this folder after
the first run. **Back this file up regularly** (just copy it somewhere safe) — if it's
deleted, the data is gone (except the 3 sample students, which get recreated automatically
on a completely fresh start).

## 🌐 Making this available to others online (not just your own computer)

Right now this only works on the computer it's running on (`localhost`). To make it
available to students and staff over the internet, you'll need to deploy it to a hosting
service (e.g. Render, Railway, a VPS, or your college's own server). This is a separate
step — let your developer/IT contact know you have a working Node.js + Express app ready
to deploy, and they can point you to the right hosting option. Ask me if you'd like help
with this when you're ready.

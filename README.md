PROJECT:- ELDERMEDIX, a voice-first medicine adherence companion for elderly people and their families 

TRACK:- Open Innovation (Healthcare) 

PROBLEM:- Many elderly people take several medicines a day on different schedules. Missed or doubled doses are common, and families often find out only after a health scare. Existing reminder apps assume a tech-comfortable user who types in every medicine by hand, in English. A missed dose usually produces a notification the user can dismiss, and nobody else knows. 

INTENDED USERS:- Elderly patients on multiple daily medicines, and their family caregivers, who are often living elsewhere. 

SOLUTION:- 
1. Photo-based setup: the user or a caregiver photographs a prescription or medicine strip, and AI extracts medicine names, dosage and timings into a schedule for confirmation. 
2. Voice-first reminders and confirmation in Hindi and English: “Did you take your BP tablet?” is answered by voice, with no typing. 
3. Escalation ladder: if a dose isn’t confirmed, the app reminds again, then alerts a family member by WhatsApp or SMS, and flags it on a caregiver dashboard. 
4. Interaction check when a new medicine is added, with a clear “confirm with your doctor or pharmacist” message. 

IMPEMENTATION APPROACH:- a mobile-friendly web app or PWA. An OCR and vision-language model handles prescription extraction, speech-to-text and text-to-speech handle voice, a backend scheduler runs reminders and escalation, and a lightweight database stores schedules and dose logs. A caregiver dashboard shows adherence history. 

SELECTED TRACKS:- 
 Frontend: React PWA with Tailwind CSS, installable on a phone Backend: Python FastAPI 
 Database and auth: Firebase Firestore and Authentication [or Supabase] 
 AI: a multimodal LLM API (for example Gemini) to read prescriptions into structured data, plus rule-based validation of dose and frequency values Voice: browser Web Speech API and SpeechSynthesis, with a cloud speech option 
 Alerts: push notifications, plus Twilio sandbox or a Telegram bot for family alerts 
 Dashboard: Recharts or Chart.js 
 
 IMPACT:- fewer missed doses, earlier caregiver awareness, and less anxiety for families. Success can be measured by confirmed-dose rate and time-to-caregiver-alert. 
 
 Built by us vs reused 
 Built:schedule logic, confirmation flow, escalation ladder, dashboard, prompts and validation 
 Reused: AI and speech APIs, messaging services, UI libraries 
 
 WORKING:- Prescription photo → AI extraction → User confirms schedule → Reminder (voice and push) → Dose confirmed? 
 Yes: log taken dose 
 No: repeat reminder → alert family contact → show on caregiver dashboard
# ELDERMEDIX — Frontend + Backend Prototype

A learning/demo prototype based on the ElderMedix project:
- React + Vite frontend
- Python FastAPI backend
- SQLite database for medicines, dose logs, and caregiver alerts
- English/Hindi browser voice reminders
- Demo prescription extraction (sample values only; no real OCR/AI)
- Demo interaction checks (not a complete or clinically validated database)

> **Safety:** This is a software prototype, not medical advice. Do not use it to manage real medication. The sample scan and interaction rules are simulated. Confirm all medicine instructions with a doctor/pharmacist. Do not enter real patient data into this demo.

## 1. Install prerequisites
Install:
- Python 3.10 or newer
- Node.js LTS (includes npm)
- Visual Studio Code

In VS Code, install the Python extension and (optionally) the ES7+ React snippets extension.

## 2. Open this project
Extract the ZIP. In VS Code choose **File → Open Folder…** and select `medmitra_vscode_project`.

## 3. Start the backend
Open **Terminal → New Terminal** in VS Code:

Windows PowerShell:
```powershell
cd backend
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
uvicorn main:app --reload
```

If PowerShell blocks activation, use Command Prompt instead:
```bat
cd backend
py -m venv .venv
.venv\Scripts\activate.bat
python -m pip install -r requirements.txt
uvicorn main:app --reload
```

Backend runs at `http://127.0.0.1:8000`.
API docs: `http://127.0.0.1:8000/docs`.
Keep this terminal open.

## 4. Start the frontend
Open a **second** VS Code terminal (Terminal → New Terminal):
```powershell
cd frontend
npm install
npm run dev
```
Open the local URL printed by Vite, usually `http://localhost:5173`.

## 5. Try the demo
- Patient tab: choose English or Hindi and press **Speak reminder**.
- **I took it** saves a confirmation to SQLite.
- **Simulate missed dose** repeats/escalates a demo reminder and eventually creates a caregiver alert.
- Caregiver tab shows medicine history and alerts.
- **Add medicine** creates a record in the backend.
- **Load sample scan** shows sample extracted fields; this is not real OCR.
- **Demo interaction check** is a tiny illustrative rule set only.

## Project structure
```text
medmitra_vscode_project/
  backend/
    main.py
    requirements.txt
  frontend/
    index.html
    package.json
    vite.config.js
    src/
      main.jsx
      App.jsx
      style.css
```

## Important limitations
- This is a local demo. It has no login/authentication, encryption, multi-user isolation, or production hosting setup.
- Browser speech depends on browser/device voice support and may require permission.
- Reminder timing is simulated by clicking buttons; no background scheduler or SMS/WhatsApp delivery is configured.
- Prescription scan and interaction check are examples only.
- Before real deployment, add authentication/authorization, privacy/security review, validated medication data, audit logs, consent, tests, and real notification/scheduling integrations.

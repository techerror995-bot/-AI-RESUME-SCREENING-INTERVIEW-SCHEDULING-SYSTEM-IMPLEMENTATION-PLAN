# -AI-RESUME-SCREENING-INTERVIEW-SCHEDULING-SYSTEM-IMPLEMENTATION-PLAN

Stack: Google Forms · Google Sheets · Google Drive · n8n · OpenAI · Telegram Bot · Gmail · Google Calendar · JavaScript

🎯 PROJECT OVERVIEW

An automated hiring system that:

collects job applications via Google Forms
downloads and extracts resume content (PDF)
uses AI to evaluate candidates
assigns score + recommendation
schedules interviews automatically for shortlisted candidates
logs everything into Google Sheets
sends notifications via Telegram + Email
🧠 SYSTEM ARCHITECTURE
📌 PHASE 1 — GOOGLE FORM SETUP
1.1 Create Application Form
Field	Type	Required
Full Name	Short Answer	✅
Email	Email	✅
Position Applied	Dropdown	✅
Resume Upload (PDF)	File Upload	✅
Cover Letter (Optional)	Paragraph	❌
1.2 Form Settings
Enable “Collect Email Addresses”
Limit to 1 response (optional)
Link to Google Sheets
📌 PHASE 2 — GOOGLE SHEETS STRUCTURE
2.1 Sheet: Applications (Auto-generated)
Column
Timestamp
Full Name
Email
Position
Resume File URL
2.2 Sheet: Candidate Log (Created manually)
Column
Name
Email
Position
Score
Recommendation
Status
Interview Date
Processed At
2.3 Sheet: Interview Schedule
Column
Candidate
Email
Date
Time
Meet Link
Status
📌 PHASE 3 — TELEGRAM BOT SETUP

Same process:

Use @BotFather → /newbot
Get Bot Token
Create HR group
Add bot as admin
Get Chat ID via getUpdates
📌 PHASE 4 — N8N MAIN WORKFLOW (25–35 NODES)
🔵 Node 1: Google Sheets Trigger
Event: New Row
Sheet: Applications
🟡 Node 2: Set Node (Map Fields)
name
email
position
resume_url
🟠 Node 3: Google Drive Download
Download resume PDF
🟣 Node 4: Extract PDF Text
Convert resume → text
🟢 Node 5: OpenAI (Message a Model)
Resume analysis → JSON output
🧠 Node 6: Parse JSON (Code Node)
📊 Node 7: IF Node (Score Check)
≥75 → Shortlist
50–74 → Review
<50 → Reject
📌 SHORTLIST FLOW
📅 Node 8: Google Calendar Create Event
Interview scheduling
Auto Meet link
📧 Node 9: Gmail Node (Invitation Email)
Send interview details
📱 Node 10: Telegram Notification (HR + Candidate)
📊 Node 11: Google Sheets Append (Log)
📌 REVIEW FLOW
⚠️ Node 12: Telegram HR Alert
📊 Node 13: Google Sheets Log Update
📌 REJECT FLOW
❌ Node 14: Gmail Rejection Email
📊 Node 15: Google Sheets Update
📌 PHASE 5 — INTERVIEW MANAGEMENT WORKFLOW
⏰ Node 16: Schedule Trigger (Daily)
📅 Node 17: Google Calendar Get Events
📱 Node 18: Telegram Daily Interview Reminder
📌 PHASE 6 — ANALYTICS WORKFLOW
📊 Node 19: Schedule Trigger (Weekly)
📊 Node 20: Google Sheets Read (All Candidates)
🧮 Node 21: Code Node (Stats Calculation)
total applicants
avg score
rejection rate
🧠 Node 22: OpenAI Summary Report
📱 Node 23: Telegram HR Report
📌 OPTIONAL ADVANCED NODES (BOOST PORTFOLIO)
Duplicate check node
Resume spam filter
AI skill matcher scoring weights
Auto follow-up email after 3 days
Candidate ranking leaderboard
📊 PHASE 7 — NODE COUNT SUMMARY
Section	Nodes
Intake System	3
File Processing	2
AI Analysis	2
Decision Logic	2
Shortlist Flow	4
Review Flow	2
Reject Flow	2
Interview System	3
Analytics System	3
TOTAL	25–35 nodes
🎓 SKILLS DEMONSTRATED

✔ AI decision systems (OpenAI)
✔ Document processing (PDF extraction)
✔ Workflow automation (n8n)
✔ API integrations (Google, Telegram, Gmail)
✔ Scheduling systems (Calendar automation)
✔ Data pipelines (Sheets logging)


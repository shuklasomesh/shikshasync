# ShikshaSync AI

**Smart school management for rural India.** Live at **[shikshasync.in](https://shikshasync.in)**.

ShikshaSync handles the daily work of a government or low-fee school, including attendance, study material,
parent messages and government reports. Everything is in Hindi and English, and parents get it on WhatsApp,
the app they already use.

> This repository is a project overview. The source code is private.

## What it does

| Area | Features |
|---|---|
| **Attendance** | One-tap roll call and biometric attendance from K30 devices (iClock protocol). Device enrolment, AI anomaly detection, and instant WhatsApp alerts to parents (present, absent or late). |
| **WhatsApp** | Parent notifications, leave approvals, fee reminders and study material, sent through the WhatsApp Business (Meta Cloud) API with a webhook for replies. |
| **AI** | Gemini-powered content generation, a doubt solver for students, and a question bank. Bhashini handles Indian-language translation. |
| **Academics** | Timetables, class tests, assessments, curriculum and subject catalogue, homework and class notices, an e-library, and teacher reports. |
| **Government compliance** | UDISE and Samagra-aligned data exports and sync. DPDP Act consent records. |
| **Roles** | Super admin, principal, teacher and parent dashboards. Google sign-in with JWT role-based access, and teacher invites. |
| **Live updates** | WebSocket notifications and an inbox. |

## Architecture

```
Next.js frontend (principal, teacher, parent)        Landing site (shikshasync.in)
            |  REST + WebSocket (JWT, Google OAuth)
Spring Boot backend: about 50 REST controllers, async jobs, caching, scheduler
     |              |                   |                    |
PostgreSQL     WhatsApp Cloud API   Gemini + Bhashini    K30 biometric devices
(Flyway)       (webhook + sends)    (AI + translation)   (iClock push protocol)
            Deployed on AWS (Docker)
```

## Tech stack

**Backend:** Java 21, Spring Boot, Spring Security (JWT, Google OAuth), PostgreSQL, Flyway, WebSockets, scheduled jobs
**Frontend:** Next.js, TypeScript, React
**Integrations:** WhatsApp Business API, Google Gemini, Bhashini, ZKTeco K30 (iClock)
**Infra:** Docker, AWS

## Built by

[Somesh Shukla](https://github.com/shuklasomesh): full-stack and AI agent developer.
Available for freelance work on [Upwork](https://www.upwork.com/freelancers/~017a42c79cd738dcf3).

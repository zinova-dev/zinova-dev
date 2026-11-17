# Proposal SaaS

A full-stack SaaS application that helps freelancers create, manage, and export professional commercial proposals.

Tech Stack: Django Ninja (Backend) · Next.js (Frontend) · PostgreSQL · Tailwind CSS

 The Problem
Freelancers waste hours formatting proposals in Word or Google Docs. This tool streamlines the process: users input their scope of work, the system calculates taxes and totals, and generates a clean PDF ready to send to clients.

 Engineering Decisions

- Backend Choice (Django over FastAPI): Chose Django Ninja because the project requires a built-in admin interface for internal operations and a mature ORM for complex relational data (Users -> Proposals -> Line Items). The async performance of FastAPI was not necessary for this CRUD-heavy workflow.
- Frontend Choice (Next.js over React+Vite):** Used Next.js for the public-facing landing page to ensure SEO optimization and fast First Contentful Paint. The authenticated dashboard leverages Next.js server components for secure data fetching.
- PDF Generation: Rejected client-side PDF generation to avoid browser inconsistencies. Implemented server-side generation using Python's `WeasyPrint` with HTML templates, ensuring consistent formatting across all devices.

 Features
- User authentication (JWT)
- CRUD for Proposals and Clients
- Tax calculation logic (Customizable per proposal)
- Server-side PDF export
- Dashboard with proposal status tracking (Draft, Sent, Accepted)

Local Setup
1. Clone the repo.
2. Backend: `cd backend && pip install -r requirements.txt && python manage.py migrate && python manage.py runserver`
3. Frontend: `cd frontend && npm install && npm run dev`
4. Set up `.env` for database credentials.

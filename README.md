## Internship Path Planner

Full-stack demo: Django backend + React frontend. Uses an A* search to map internship transitions toward a target role using the provided `internships.csv` dataset.

### Requirements
- Python 3.10+ with `pip`
- Node 18+ with `npm`
- OS: tested on Windows 10

### Backend setup (Django)
From the repo root:
1) Install deps  
   `pip install -r backend/requirements.txt`
2) Apply migrations  
   `python backend/manage.py migrate`
3) Load the dataset (uses `internships.csv` in the repo root)  
   `python backend/manage.py load_internships`
4) Run the server (defaults to port 8000)  
   `python backend/manage.py runserver`

### Frontend setup (React)
1) Install deps  
   `cd frontend && npm install`
2) Start the dev server (defaults to port 3000)  
   `npm start`
3) (Optional) Point the UI to a different API base: set `REACT_APP_API_URL`, e.g. `http://localhost:8000/api`.

### API quick reference
- `POST /api/path/`  
  Body: `{ "skills": ["python", "sql"], "target_role": "data scientist intern", "location": "new york" }`  
  Returns: A* selected path with cost breakdown and skill accrual.
- `GET /api/internships/` (optional `?location=` filter)

### Notes
- Default DB is SQLite at `backend/db.sqlite3`.
- Admin is enabled; you can create a superuser if needed: `python backend/manage.py createsuperuser`.








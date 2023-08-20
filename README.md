# JobSpy Scraper

## Features

- Scrapes job postings from **LinkedIn**, **Indeed**, **ZipRecruiter**
- Returns jobs with title, location, company, and other data
- JWT authorization
  
![jobspy](https://github.com/cullenwatson/jobspy/assets/78247585/a0dd2154-2ab8-4378-a44e-9d7c51db1293)

## Endpoints
![image](https://github.com/JobSpy-ai/backend/assets/78247585/dd619564-d7cb-4a93-8937-33e0beb0fb6a)

### Jobs Endpoint

**Endpoint**: `/api/v1/jobs/`

#### Parameters:
- **site_type**: str (Required) - Options: `linkedin`, `zip_recruiter`, `indeed`
- **search_term**: str (Required)
- **location**: int
- **distance**: int
- **job_type**: str - Options: `fulltime`, `parttime`, `internship`, `contract`
- **is_remote**: bool
- **results_wanted**: int
- **easy_apply**: bool (Only for LinkedIn)

## Installation
_Python >= 3.10 required_  
1. Clone this repository
2. Install the dependencies with `pip install -r requirements.txt`
3. Add `.env` with variables from above
4. Run the server with `uvicorn main:app --reload`

## Usage

Visit [http://localhost:8000/docs](http://localhost:8000/docs) to see the interactive API documentation.

## FAQ

### I'm having issues with my queries. What should I do?

Broadening your filters can often help. Additionally, try reducing the number of `results_wanted`.  
If issues still persist, feel free to submit an issue.

### How to enable auth?

Change `AUTH_REQUIRED` in `/settings.py` to `True`

The auth uses [supabase](https://supabase.com). Create a project with a `users` table and disable RLS.
<img src="https://github.com/JobSpy-ai/backend/assets/78247585/d6ebf4f3-962f-4a91-b484-d610bd3f15fc" width="500">

Add these three environment variables:

- `SUPABASE_URL`: go to project settings -> API -> Project URL  
- `SUPABASE_KEY`: go to project settings -> API -> service_role secret
- `JWT_SECRET_KEY` - type `openssl rand -hex 32` in terminal to create a 32 byte secret key

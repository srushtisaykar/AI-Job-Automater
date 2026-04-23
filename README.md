# Job Application Automation with AI and n8n

## Overview

This repository contains an automated workflow designed to streamline job application processes. Built using [n8n](https://n8n.io/), this workflow accepts a user's resume, extracts relevant data using AI, matches it against job listings, and rewrites the resume to match job descriptions. Updated resumes are then stored in Google Drive and tracked in a centralized Google Sheet.

## Features

* Accepts resume uploads via a frontend webhook
* Uses AI to extract structured personal information from resumes
* Automatically creates folders and sheets in Google Drive and Google Sheets
* Searches job portals using an external API (e.g., Apify + Naukri Scraper)
* Rewrites the resume to match specific job roles using AI (LangChain agents)
* Uploads the generated resume to cloud storage and updates tracking sheets

## Workflow Highlights

1. **Frontend Webhook**

   * Accepts job role, experience, location, GitHub, LinkedIn, and resume file.

2. **Resume Extraction**

   * Extracts raw text from uploaded PDF files.
   * Uses AI (DeepSeek via LangChain) to parse name, address, email, education.

3. **Google Integration**

   * Stores user data in a centralized Google Sheet.
   * Creates a personal sheet and folder for each applicant in Google Drive.

4. **Job Matching**

   * Uses predefined search parameters (role, experience, location).
   * Calls Apify API to fetch jobs from Naukri and process results.

5. **Resume Generation**

   * For each job:

     * Rewrites resume using AI based on job title, description, and skills.
     * Formats content into an ATS-optimized resume template.

6. **Document Storage**

   * Converts AI-generated text into a file.
   * Uploads the file to Google Drive.
   * Adds a shareable link back to the tracking sheet.

## Requirements

* n8n (Self-hosted or Cloud)
* Apify account (with access to Naukri scraper or similar actor)
* Google Drive and Google Sheets API credentials
* Resume PDF (uploaded via webhook or frontend form)

## Setup Instructions

1. **Clone this Repository**

   ```bash
   git clone https://github.com/srushtisaykar/job-app.git
   ```

2. **Configure n8n**

   * Import the `Job_App.json` into your n8n instance.
   * Set up credentials for:

     * Google Sheets
     * Google Drive
     * HTTP Request (if API keys are needed)

3. **Frontend Integration**

   * Integrate with a basic form to collect:

     * Name
     * Resume (PDF)
     * Job preferences (title, location, experience)
     * GitHub and LinkedIn links

4. **Environment Variables**
   Ensure your n8n environment has appropriate API tokens (e.g., Apify, Google).

## Output

* Personalized and rewritten resumes
* Centralized Google Sheet logging user and job data
* Google Drive folder for each user storing all updated resumes


## Author

Created by srushti saykar

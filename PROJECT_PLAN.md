# ApplyTrack Project Plan

## 1. Problem Statement

People applying for academic and professional positions often store
information across emails, spreadsheets, bookmarks, documents, and notes.

This makes it difficult to track deadlines, required documents, application
status, and upcoming actions.

ApplyTrack will provide one place where users can organize opportunities,
prepare their applications, and track their results.

## 2. Target User

The initial target user is an individual applicant searching for opportunities
such as:

- PhD positions
- Postdoctoral positions
- Academic jobs
- Scholarships
- Research internships
- Industry positions

Users find opportunities on different websites. They need to save the advertisement, deadline, institution, required documents, and current application status. 

## 3. Project Objective

The objective of ApplyTrack is to build a secure and responsive web application in which users can save opportunities, manage application
requirements, track deadlines, update application statuses, and review their overall application progress.

## 4. Main User Workflow 
1. The visitor creates an account.
2. The user logs in.
3. The user saves an opportunity.
4. The user reviews the opportunity.
5. The user decides to apply.
6. The user creates an application record.
7. The user adds the application requirements.
8. The user marks requirements as completed.
9. The user submits the application.
10. The user updates its status.
11. The user records interviews, offers, or rejections.
12. The user reviews progress on the dashboard.

## 5. Minimum Viable Product

### User Accounts

- Register
- Log in
- Log out
- Access private user data

### Opportunity Management

- Add an opportunity
- View an opportunity
- Edit an opportunity
- Delete an opportunity
- Search opportunities
- Filter opportunities


### Application Management

- Convert an opportunity into an application
- Record the current application status
- Add submission, interview, and follow-up dates
- Add personal notes

### Requirements

- Add application requirements
- Mark requirements as completed
- Delete requirements
- Show application preparation progress

### Dashboard

- Show saved opportunities
- Show submitted applications
- Show upcoming deadlines
- Show interviews and offers

### JavaScript Features

- Update a requirement without reloading the page
- Update application status without reloading the page
- Update the progress indicator
- Show deadline warnings

### Responsive Design

- Desktop layout
- Tablet layout
- Mobile layout

## 6. Features Excluded from Version 1

- Job-board scraping
- Artificial intelligence features
- Automatically generated cover letters
- Email reminders
- Google Calendar integration
- Real-time chat
- Social networking
- Recruiter accounts
- React
- Mobile application
- Payment processing


## 7. Functional Requirements

### FR-01: Registration

A visitor must be able to create an account using a username, email address,
password, and password confirmation.

### FR-02: Authentication

A registered user must be able to log in and log out.

### FR-03: Data Privacy

A user must only be able to view and modify their own records.

### FR-04: Opportunity Creation

A user must be able to save a new opportunity.

### FR-05: Opportunity Management

A user must be able to view, edit, and delete their opportunities.

### FR-06: Search and Filtering

A user must be able to search and filter their saved opportunities.

### FR-07: Application Creation

A user must be able to create an application associated with an opportunity.

### FR-08: Status Management

A user must be able to update the status of an application.

### FR-09: Requirement Management

A user must be able to add, complete, and delete application requirements.

### FR-10: Dashboard

A user must be able to view application statistics and upcoming deadlines.

### FR-11: JavaScript Updates

Important status and checklist actions should work without fully reloading the
page.

### FR-12: Responsive Layout

The application must remain usable on desktop and mobile screens.

### US-13 
As a user, I want to record a follow-up date so that I know when to contact the institution after submitting an application

### US-14

As a user, I want to add personal notes to an application so that I can record important details about the position, interview, or application process.

## 8. Non-Functional Requirements

### Security

- Passwords must be handled using Django authentication.
- Users must not access another user's data.
- Forms must use CSRF protection.
- Server-side validation must be used.
- Secret information must not be committed to GitHub.

### Usability

- Navigation should be consistent.
- Forms should display understandable errors.
- Important operations should show success or failure feedback.
- The interface should work without horizontal scrolling on mobile devices.

### Reliability

- Invalid information must not be saved.
- Missing records should produce a 404 response.
- Destructive operations must require confirmation.
- JavaScript failures should show an error message.

### Performance

- Long lists should use pagination.
- Database queries should only retrieve the current user's records.
- The project should avoid unnecessary repeated database queries.

## 9. User Stories


### US-01

As a visitor, I want to register so that I can create a private application
tracker.

### US-02

As a registered user, I want to log in so that I can access my saved
information.

### US-03

As a user, I want to save an opportunity so that I do not lose its details.

### US-04

As a user, I want to edit an opportunity so that I can keep its information
current.

### US-05

As a user, I want to search by title or institution so that I can find an
opportunity quickly.

### US-06

As a user, I want to sort opportunities by deadline so that I can prioritize
urgent applications.

### US-07

As a user, I want to convert an opportunity into an application so that I can
track its preparation.

### US-08

As a user, I want to add required materials so that I know what I need to
prepare.

### US-09

As a user, I want to mark requirements as complete so that I can monitor my
progress.

### US-10

As a user, I want to update the application status so that I know its current
stage.

### US-11

As a user, I want to see approaching deadlines so that I do not miss them.

### US-12

As a user, I want my records to remain private so that another user cannot
access them.

## 10. Application Statuses

| Status | Meaning |
|---|---|
| Saved | The opportunity has been saved but not fully reviewed |
| Reviewing | The user is examining the opportunity |
| Preparing | The application materials are being prepared |
| Submitted | The application has been submitted |
| Interview | The applicant has received an interview invitation |
| Rejected | The application was unsuccessful |
| Offer | The applicant has received an offer |
| Accepted | The applicant accepted the offer |
| Withdrawn | The applicant decided not to continue |

## 11. Initial Data Entities


### Opportunity

- Owner
- Title
- Institution
- Country
- Opportunity type
- Deadline
- Advertisement URL
- Description
- Priority
- Funding status
- Creation date
- Last update date

### Application

- Related opportunity
- Status
- Submission date
- Interview date
- Follow-up date
- Notes
- Creation date
- Last update date

### Requirement

- Related application
- Title
- Completion status
- Due date
- Creation date

## 12. Data Relationships

- One User can own many Opportunities.

- One Opportunity belongs to one User.

- One Opportunity can have zero or one Application.

- One Application belongs to one Opportunity.

- One Application can have many Requirements.

- One Requirement belongs to one Application.

A visual presentations: 

```text
User
  │
  └── Opportunity
        │
        └── Application
              │
              ├── Requirement
              ├── Requirement
              └── Requirement
```
### Relation types

User 1 ───── many Opportunities
Opportunity 1 ───── 0 or 1 Application

## 13. Business Rules

1. Every opportunity must belong to one user.

2. A user can only view or modify their own opportunities.

3. An application must belong to an opportunity.

4. An opportunity can have no more than one application in Version 1.

5. A requirement must belong to an application.

6. The application status must be one of the supported status choices.

7. A deadline may be empty when it is unknown.

8. A user cannot submit arbitrary application status text through JavaScript.

9. Deleting an opportunity must require confirmation.

10. Deleting an opportunity may also delete its associated application and
requirements.

11. Application progress is based on the percentage of completed requirements.

12. When an application has no requirements, the interface should display
"No requirements added" rather than 100% complete.

Progress percentage =
(completed requirements / total requirements) × 100

## 14. Pages and Routes

### Public Pages

- Home page
- Registration page
- Login page

### Protected Pages

- Dashboard
- Opportunity list
- Opportunity details
- Create opportunity
- Edit opportunity
- Delete opportunity
- Application list
- Application details
- Edit application
- Delete application
- Profile page

## 15. Interface Wireframes

+------------------------------------------------------+
| ApplyTrack   Dashboard   Opportunities   Logout      |
+------------------------------------------------------+

+------------+ +------------+ +------------+
| Saved: 10  | | Applied: 5 | | Interviews:2|
+------------+ +------------+ +------------+

Upcoming Deadlines
--------------------------------------------------------
Position                 Institution          Deadline
PhD in AI                University A         Aug 20
Research Assistant       University B         Aug 25
--------------------------------------------------------

### Opportunity list wireframe 

+------------------------------------------------------+
| Search: [_____________] Type: [All] Sort: [Deadline] |
+------------------------------------------------------+

+-----------------------------------------------------+
    Position    |   Institution |   Country | Deadline
+-----------------------------------------------------+
                |               |           |           
                |               |           |



[View] [Edit] [Delete]

### Application details wireframe

Postdoctoral Researcher in Coding Theory
Example University

Status: Preparing
Deadline: August 30, 2026
Progress: 75%

Requirements
[x] CV
[x] Cover letter
[x] Transcript
[ ] Recommendation letter

[Add Requirement]

## 16. Technology Stack

| Part | Technology |
|---|---|
| Backend language | Python |
| Backend framework | Django |
| Frontend structure | HTML |
| Frontend styling | CSS and Bootstrap |
| Frontend programming | Vanilla JavaScript |
| Database language | SQL |
| Development database | SQLite |
| Production database | PostgreSQL |
| Version control | Git and GitHub |
| Testing | Django testing framework |

The first version will use Django templates and vanilla JavaScript. React will
not be used because the goal is to strengthen Django, JavaScript, DOM, Fetch
API, and server-rendered application skills first.


```
The first version will use Django templates and vanilla JavaScript. React will not be used because the goal is to strengthen Django, JavaScript, DOM, Fetch API, and server-rendered application skills first.
```
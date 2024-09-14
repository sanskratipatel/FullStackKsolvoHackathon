# FullStackKsolvoHackathon  

# Event Management System

## Overview

The **Event Management System** is a web application built using Django to facilitate the creation, management, and participation in events. The system allows users to create events, RSVP to them, view event details, and manage their activities. It supports user authentication, scheduling, notifications, and provides a responsive and scalable design.

This document outlines the project setup, folder structure, file descriptions, and implementation steps.

## Features

- Event creation and management
- User registration and authentication
- Event scheduling
- RSVP system
- Notification system
- Activity tracking for users
- Admin interface for event management
- Responsive user interface

---

## Project Structure

```bash
event_management_system/
├── event_management_system/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── events/
│   ├── migrations/
│   │   └── __init__.py
│   ├── static/
│   │   └── events/
│   │       ├── css/
│   │       │   └── styles.css
│   │       └── js/
│   │           └── scripts.js
│   ├── templates/
│   │   └── events/
│   │       ├── base.html
│   │       ├── event_list.html
│   │       ├── event_detail.html
│   │       └── create_event.html
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── templates/
│   └── registration/
│       ├── login.html
│       └── signup.html
├── static/
│   └── css/
│       └── global.css
├── manage.py
└── db.sqlite3
```

---

## File Descriptions

### Project Configuration

- `event_management_system/__init__.py`: Marks the directory as a Python package.
- `event_management_system/settings.py`: Django settings and configuration for database, apps, middleware, and static files.
- `event_management_system/urls.py`: Root URL routing for the project, directing to app-specific URLs.
- `event_management_system/wsgi.py`: WSGI configuration for project deployment.
- `event_management_system/asgi.py`: ASGI configuration for handling asynchronous operations.

### Application Configuration

- `events/models.py`: Defines models to represent events, users, and their relationships.
- `events/views.py`: Contains view functions or class-based views for handling HTTP requests, rendering templates, and processing data.
- `events/urls.py`: Configures URL routing specific to the `events` application.
- `events/admin.py`: Configures the Django admin interface for managing event data.
- `events/apps.py`: Contains application-specific configuration.
- `events/templates/events/`: Contains HTML templates for event creation, viewing, and listings.
- `events/static/events/`: Static files (CSS/JS) specific to the `events` application.

### User Authentication

- `templates/registration/login.html`: Template for user login.
- `templates/registration/signup.html`: Template for user signup.

### Static Files

- `static/css/global.css`: Global styles applied across the project.
- `events/static/events/css/styles.css`: Styles specific to the `events` application.
- `events/static/events/js/scripts.js`: JavaScript specific to the `events` application.

### Database

- `db.sqlite3`: SQLite database used for development.

### Management

- `manage.py`: Utility for managing the Django project, running server, migrations, and more.

---

## Implementation Steps

### A. Setup the Project

1. **Create a Django Project**:  
   Initialize the Django project and the `events` application.
   ```bash
   django-admin startproject event_management_system
   cd event_management_system
   python manage.py startapp events
   ```

2. **Configure Settings**:  
   Update `settings.py` to include the `events` app, configure database settings, static files, and middleware.

3. **Set Up URLs**:  
   In `event_management_system/urls.py`, define URL patterns and include routes for the `events` app.

### B. Develop the Application

1. **Define Models**:  
   Define data models in `events/models.py` for managing events and user relationships.
   ```python
   class Event(models.Model):
       name = models.CharField(max_length=100)
       date = models.DateTimeField()
       location = models.CharField(max_length=255)
       description = models.TextField()
   ```

2. **Implement Views**:  
   Add views in `events/views.py` to handle event creation, listing, and detailed view.
   ```python
   def event_list(request):
       events = Event.objects.all()
       return render(request, 'events/event_list.html', {'events': events})
   ```

3. **Create Templates**:  
   Design HTML templates (`event_list.html`, `event_detail.html`, etc.) for event-related user interfaces.

4. **Configure Static Files**:  
   Organize static files in the `static/` and `events/static/events/` directories for styling and JavaScript.

### C. Database and Migrations

1. **Create Migrations**:  
   Generate and apply migrations to update the database schema based on the defined models.
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

2. **Seed Database** (Optional):  
   Optionally, populate the database with initial data for testing.

### D. User Authentication

1. **Create Authentication Templates**:  
   Develop `login.html` and `signup.html` templates for user authentication.

2. **Set Up Authentication Views**:  
   Use Django's built-in authentication views and forms to handle user login and registration.


## Evaluation Criteria

- **Coding Practices**: Code should be modular, well-structured, and follow Django best practices.
- **System Design**: Ensure the design is scalable with a clear separation of concerns.
- **Functionality**: All core features (event creation, listing, RSVP, etc.) should work correctly.
- **Performance**: Assess application responsiveness and load time.
- **Security**: Implement proper user data protection and authentication.
- **Containerization (Optional)**: Use Docker for containerization if desired for easier deployment.

---

## Setup Instructions

1. **Clone the Repository**:  
   ```bash
   git clone <repo_url>
   cd event_management_system
   ```

2. **Install Dependencies**:  
   Install necessary packages using pip:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run Migrations**:  
   Set up the database and apply migrations:
   ```bash
   python manage.py migrate
   ```

4. **Run the Development Server**:  
   Start the Django development server:
   ```bash
   python manage.py runserver
   ```

5. **Access the Application**:  
   Open your web browser and go to `http://127.0.0.1:8000/` to interact with the application.

---


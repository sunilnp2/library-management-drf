# Library Management System API

This Django REST Framework (DRF) project manages a library system with features like registration, authentication book listing, borrowing, and returning.
with complete unit testing of models, serializer, and views.

## Table of Contents

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Server](#running-the-server)
- [API Documentation](#api-documentation)
  - [Endpoint 1: Signup](#http://localhost:8000/auth/api/signup/)
  - [Endpoint 1: Get All User](#http://localhost:8000/auth/api/getalluser/)
  - [Endpoint 1: Login](#http://localhost:8000/auth/api/login/)
  - [Endpoint 1: List All Books](#endpoint-1-list-all-books)
  - [Endpoint 2: Borrow Book](#endpoint-2-borrow-book)
  - [Endpoint 3: Return Borrowed Book](#endpoint-3-return-borrowed-book)

## Getting Started

### Prerequisites

Make sure you have the following tools installed:

- Python (>=3.x)
- Django
- Django REST Framework

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/sunilnp2/library-management-drf.git
   cd library-management-drf

2. Install dependencies:

    ```bash
    pip install -r requirements.txt

3. Configure Database
  
   ```bash
     PostgreSQL Database
     DATABASES = {
     'default': {
         'ENGINE': 'django.db.backends.postgresql',
         'NAME': 'lms', # your database name
         'USER': 'sunil', #user db user
         'PASSWORD': 'sunil', #user password
         'HOST': '127.0.0.1',
         'PORT': '5432',
     }
    }

   For Sqlite Database
       DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / "db.sqlite3",
        }
    }

   

4. Apply database migrations:
    ```bash
    Windows
    python manage.py makemigrations
    python manage.py migrate

    Linux
    python3 manage.py makemigrations
    python3 manage.py migrate
    
5. Create Superuser:
    ```bash
    python manage.py createsuperuser

    python3 manage.py createsuperuser
    
    test@gmail.com
    test123

6. Start the development server:
    ```bash
    python manage.py runserver

    python3 manage.py runserver
The API will be accessible at http://localhost:8000


## API Documentation

### API Endpoint: Create a New User

- **URL:** `http://localhost:8000/auth/api/signup/`
- **Method:** POST
- **Authentication:** No Auth
- **Data:**

  ```json
  {
    "name": "Sunil Nepali",
    "email": "sunil@gmail.com",
    "password": "test123"
    "password2": "test123"
  }

### API Endpoint: Login

- **URL:** `http://localhost:8000/auth/api/login/`
- **Method:** POST
- **Authentication:** No Auth
- **Data:**

  ```json
  {
  "email": "sunil@gmail.com",
  "password": "test123"
  }

### API Endpoint: Get All User

- **URL:** `http://localhost:8000/auth/api/getalluser/`
- **Method:** Get
- **Authentication:** No Auth

### API Endpoint: Get Specific User User

- **URL:** `http://localhost:8000/auth/api/getuser/id/`
- **Method:** Get
- **Authentication:** No Auth

### API Endpoint: Create a New Book

- **URL:** `http://localhost:8000/library/api/book_all_create/`
- **Method:** POST
- **Authentication:** Basic Authentication
- **Permissions:** CustomPermission - (IsAuthenticatedOrReadOnly)
- **Data:**

  ```json
  {
    "title": "Rich Dad Poor Dad",
    "isbn": "4354",
    "published_date": "2020-04-23"
    "genre": "finance"
  }

### API Endpoint: Get All Books

- **URL:** `http://localhost:8000/library/api/book_all_create/`
- **Method:** Get
- **Authentication:** No Auth

  
### API Endpoint: Get Specific Books

- **URL:** `http://localhost:8000/library/api/book/id`
- **Method:** Get
- **Authentication:** No Auth


### API Endpoint: Create a Book Detail

- **URL:** `http://localhost:8000/library/api/create-book-detail/`
- **Method:** POST
- **Authentication:** Basic Auth
- **Permissions:** CustomPermission - (IsAuthenticatedOrReadOnly)
- **Data:**

  ```json
  {
    "book": 1,
    "number_of_pages": 330,
    "publisher": "Asmita Publication",
    "language": "english"
  }

### API Endpoint: Update Book Detail

- **URL:** `http://localhost:8000/library/api/book-detail/id/`
- **Method:** Patch
- **Authentication:** Basic Auth
- **Permissions:** CustomPermission - (IsAuthenticatedOrReadOnly)
- **Data:**

  ```json
  {
    "number_of_pages": 400,
  }


### API Endpoint: Borrow Book

- **URL:** `http://localhost:8000/library/api/borrowbook/`
- **Method:** POST
- **Authentication:** Basic Auth
- **Permissions:** CustomPermission - (IsAuthenticatedOrReadOnly)
- **Data:**

  ```json
  {
    "user": 1, 
    "book": 1,
  }

  
### API Endpoint: List Borrowed Books

- **URL:** `http://localhost:8000/library/api/list_borrowed_book/`
- **Method:** Get
- **Authentication:** Basic Auth
- **Permissions:** CustomPermission - (IsAuthenticatedOrReadOnly)

### API Endpoint: Return Borrowed Book

- **URL:** `http://localhost:8000/library/api/return-book/id/`
- **Method:** Put
- **Authentication:** Basic Auth
- **Permissions:** CustomPermission - (IsAuthenticatedOrReadOnly)
- **Data:**

  ```json
  {
    "returned_date": "2024-02-01"
  }


  

  










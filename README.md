# FlowFin Backend API

FlowFin Backend is the core **FastAPI powered service** for the FlowFin platform, a system designed to automate and streamline **supply chain financing**.

The backend provides **secure and scalable endpoints** for managing users, processing financial operations, and enabling real-time financing workflows.

---

## 🧩 Problem Statement

Design and develop a **robust backend service** to manage the core operations of a supply chain financing platform.

The system must handle:

* Secure user authentication
* Database connectivity for financial data
* A clean API for front-end applications to process invoices, manage users, and facilitate financing workflows.

---

## 🚀 Features

* **Secure User Authentication:** Full sign-up, sign-in, and sign-out workflow using JWT.
* **Token Management:** Uses `access_token` and `refresh_token` for secure API access, including an endpoint for token refreshing.
* **Secure Sign-out:** Implements a token blacklist to securely invalidate tokens upon user sign-out.
* **Password Hashing:** Uses `bcrypt` for securely hashing and verifying user passwords.
* **Database Integration:** Uses SQLAlchemy ORM for robust connectivity to a PostgreSQL database.
* **Schema Validation:** Leverages Pydantic for strict request and response data validation.
* **Async Support:** Built with FastAPI for high-performance, asynchronous request handling.
* **CORS Enabled:** Pre-configured with CORS middleware to allow cross-origin requests.

---

## 🔐 Authentication

The API uses **JWT Bearer Tokens** for authenticating user-protected endpoints.

Include the following header in your requests after signing in:

```http
Authorization: Bearer <token>
```

---

## 📚 Endpoints

### Auth Endpoints

| Method | Endpoint              | Description                                       |
| ------ | --------------------- | ------------------------------------------------- |
| POST   | `/auth/sign_up`       | Create a new user account.                        |
| POST   | `/auth/sign_in`       | Authenticate and receive access/refresh tokens.   |
| POST   | `/auth/refresh_token` | Refresh access token using a valid refresh token. |
| POST   | `/auth/sign_out`      | Revoke tokens (via blacklisting) and sign out.    |

### Default Endpoints

| Method | Endpoint | Description                                 |
| ------ | -------- | ------------------------------------------- |
| GET    | `/`      | Root endpoint for API health/status checks. |

---

## 🧱 Schemas

Key **Pydantic models** used for data validation:

* `UserCreate`: Payload for new user registration *(email, password)*
* `UserLogin`: Payload for user sign-in *(email, password)*
* `RefreshToken`: Payload for refreshing an access token
* `Token`: Response model containing `access_token` and `refresh_token`
* `UserOut`: Response model for user details *(id, email, is_active)*

---

## ⚙️ Installation & Setup

### Requirements

* Python 3.8+
* FastAPI
* SQLAlchemy
* PostgreSQL
* python-dotenv, passlib[bcrypt], python-jose[cryptography]

### Steps

```bash
# Clone repository
git clone <repository-url>
cd flowfin_backend

# Install dependencies
# (Assuming a requirements.txt file exists)
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env
# Edit .env with your database & secret config

# Run server
uvicorn main:app --reload
```

**API will be available at:** [http://localhost:8000](http://localhost:8000)
**Interactive docs will be available at:** [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 💜 Made with Love

Made with 💜 by:

* [Pratyaksh Kwatra](https://github.com/pratyakshkwatra)
* [Harshita Aggarwal](https://github.com/harshitaaggarwall)
* [Manya Jain](https://github.com/Manyajain10-abc)
* [Kanishka Upadhyay](https://github.com/kanishkaupadhyay08)

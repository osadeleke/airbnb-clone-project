# 🏠 Airbnb Clone Backend

## Introduction

**Airbnb Clone Backend** is a robust and scalable backend system designed to power an Airbnb-style application. It handles core functionalities such as user management, property listings, bookings, payments, and reviews. Built with **Django**, **Django REST Framework**, and **PostgreSQL**, it leverages **GraphQL**, **Celery**, **Redis**, and **Docker** to ensure high performance, flexibility, and smooth deployment.

## 👥 Team Roles and Responsibilities

### 🧑‍💻 Backend Developer
Responsible for implementing the server-side logic, APIs, and database models. They develop and maintain the RESTful and GraphQL endpoints, ensuring that all features - from user management to bookings - function efficiently and securely.

### 🗄️ Database Administrator (DBA)
Manages the design, optimization, and maintenance of the **PostgreSQL** database. The DBA ensures data integrity, implements indexing and caching strategies, and optimizes queries for performance and scalability.

### ⚙️ DevOps Engineer
Handles deployment automation, continuous integration, and delivery pipelines using tools like **Docker** and **CI/CD**. They manage cloud infrastructure, monitor system performance, and ensure reliability and scalability in production environments.

### 🧪 QA Engineer
Ensures the backend system meets quality standards by designing and executing tests for APIs, performance, and security. The QA Engineer identifies bugs early in the development cycle and collaborates with developers to maintain a stable, reliable product.

### 👨‍🏫 Project Manager
Coordinates communication between team members, manages timelines, and ensures that project goals are met. The PM tracks progress, mitigates risks, and aligns the team with the overall project vision.

## ⚙️ Technology Stack

The **Airbnb Clone Backend** leverages a modern and scalable technology stack to ensure reliability, performance, and maintainability across all backend services.

### 🐍 Django
A high-level Python web framework used to build the core backend logic and RESTful APIs. It provides rapid development, clean design, and robust security features.

### 🌐 Django REST Framework (DRF)
An extension of Django that simplifies the creation of RESTful APIs. It handles serialization, authentication, and permissions while offering powerful tools for API development.

### 🗃️ PostgreSQL
A reliable and feature-rich relational database system used for storing and managing structured data such as user profiles, property listings, and bookings.

### 🔍 GraphQL
A query language for APIs that allows clients to request specific data, improving efficiency and flexibility compared to traditional REST endpoints.

### ⚡ Celery
A distributed task queue used to handle asynchronous operations such as sending notifications, processing background jobs, and managing payment workflows.

### 🧠 Redis
An in-memory data store used for caching, session management, and queuing tasks. It enhances application speed and reduces database load.

### 🐳 Docker
A containerization platform that ensures consistent development and deployment environments. It simplifies setup, scaling, and maintenance of backend services.

### 🚀 CI/CD Pipelines
Automated continuous integration and deployment pipelines that streamline testing, building, and deploying code changes, ensuring rapid and reliable delivery of new features.

## 🗄️ Database Design

The **Airbnb Clone Backend** is structured around several core entities that model users, properties, bookings, reviews, and payments. The database design ensures data consistency, scalability, and easy integration with both RESTful and GraphQL APIs.

### 👤 Users
**Description:** Represents individuals who can act as guests or hosts within the platform.  
**Key Fields:**
- `id` – Unique identifier for each user.  
- `username` – The user's display or login name.  
- `email` – Used for authentication and communication.  
- `password_hash` – Securely stored password hash.  
- `role` – Defines whether the user is a host, guest, or admin.  

**Relationships:**
- A **user** can list multiple **properties**.  
- A **user** can make multiple **bookings**.  
- A **user** can write multiple **reviews**.

---

### 🏡 Properties
**Description:** Represents properties listed by hosts for rental.  
**Key Fields:**
- `id` – Unique identifier for each property.  
- `title` – Name or headline for the property.  
- `description` – Detailed information about the property.  
- `price_per_night` – Cost of renting per night.  
- `host_id` – Foreign key linking to the user who owns the property.  

**Relationships:**
- A **property** belongs to one **user (host)**.  
- A **property** can have multiple **bookings** and **reviews**.

---

### 📅 Bookings
**Description:** Represents reservations made by guests for specific properties.  
**Key Fields:**
- `id` – Unique booking identifier.  
- `user_id` – Foreign key referencing the guest who made the booking.  
- `property_id` – Foreign key referencing the booked property.  
- `check_in` – Start date of the booking.  
- `check_out` – End date of the booking.  

**Relationships:**
- A **booking** belongs to one **user (guest)**.  
- A **booking** is linked to one **property**.  
- A **booking** can have one **payment record**.

---

### 💳 Payments
**Description:** Tracks payment transactions for property bookings.  
**Key Fields:**
- `id` – Unique payment identifier.  
- `booking_id` – Foreign key linking to the related booking.  
- `amount` – Total payment amount.  
- `payment_status` – Status of the payment (e.g., pending, completed, failed).  
- `timestamp` – Date and time of the transaction.  

**Relationships:**
- A **payment** is associated with one **booking**.  
- A **booking** can have one **payment**.

---

### ⭐ Reviews
**Description:** Allows guests to leave feedback and ratings for properties they’ve stayed in.  
**Key Fields:**
- `id` – Unique review identifier.  
- `user_id` – Foreign key referencing the reviewer.  
- `property_id` – Foreign key referencing the reviewed property.  
- `rating` – Numeric score given by the guest.  
- `comment` – Text feedback from the guest.  

**Relationships:**
- A **review** belongs to one **user (guest)**.  
- A **review** belongs to one **property**.  
- A **property** can have multiple **reviews**.

---

### 🔗 Entity Relationships Summary
- **User → Property:** One-to-Many  
- **User → Booking:** One-to-Many  
- **User → Review:** One-to-Many  
- **Property → Booking:** One-to-Many  
- **Property → Review:** One-to-Many  
- **Booking → Payment:** One-to-One

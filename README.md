
# Secure Login and Registration System  

This project is a secure login and registration system built using **Node.js**, **Express.js**, **PostgreSQL**, and **bcrypt** for password hashing. It ensures safe storage of user passwords and allows users to register and log in securely.

## Features  
- User registration with email and password.  
- Password hashing with **bcrypt** for secure storage.  
- Login functionality with validation.  
- Database integration with PostgreSQL.  


## Installation  

1. **Clone the Repository**  
   ```bash
   git clone <repository-url>
 

2.  **Install Dependencies**  
    Run the following command to install the required Node.js packages:
    
    ```bash
    npm install
    
    ```
    -   -   `);` 
        
-   **Configure Environment Variables**  
    Create a `.env` file in the root directory and add the following variables:
    
    env
    
    Copy code
    
    `PORT=3000
    user:  process.env.PG_USER,
    host:  process.env.PG_HOST,
   database:  process.env.PG_DATABASE,
   password:  process.env.PG_PASSWORD,
   port:  process.env.PG_PORT,
    
    **Environment Variables Used in This Repository**:
    
    
    -   `PG_HOST`: The hostname or IP address of the PostgreSQL server.
    -   `PG_USER`: The username for connecting to the PostgreSQL database.
    -   `PG_PASSWORD`: The password for the PostgreSQL user.
    -   `PG_DATABASE`: The name of the PostgreSQL database.
    -   `PG_PORT`: The port on which PostgreSQL is running (default: 5432).
    -   hashing (default: 10).
    -   `SESSION_SECRET`: A unique, secure string used for signing session cookies.
    
3.  **Set Up PostgreSQL Database**
    
    -   Create a PostgreSQL database (e.g., secrets`).
    -   Run the following SQL commands to set up the `users` table:
        
        ```sql
        CREATE TABLE users (
            id SERIAL PRIMARY KEY,
            email VARCHAR(255) UNIQUE NOT NULL,
            password VARCHAR(255) NOT NULL
        );
        
        ```

    ```
    
5.  **Run the Application**  
    Start the server:
    
    ```bash
    npm start
    
    ```
    
    The application will run on `http://localhost:3000`.
    

## Endpoints

### 1. **Register**

-   **URL**: `/register`
-   **Method**: POST
-   **Body**:
    
    ```json
    {
        "email": "user@example.com",
        "password": "password123"
    }
    
    ```
    
-   **Process**:
    -   The password is hashed using `bcrypt` before being stored in the database.

### 2. **Login**

-   **URL**: `/login`
-   **Method**: POST
-   **Body**:
    
    ```json
    {
        "email": "user@example.com",
        "password": "password123"
    }
    
    ```


## Technologies Used

-   **Node.js**: Backend runtime environment.
-   **Express.js**: Web framework for Node.js.
-   **PostgreSQL**: Database for storing user data.
-   **bcrypt**: For securely hashing and comparing passwords.


## Folder Structure

```

├── views/  
│   ├── login.ejs       # Login page  
│   ├── register.ejs    # Registration page  
├── public/  
│   ├── css/            # Stylesheets  
├── app.js              # Main application file  
├── package.json        # Project dependencies  

```

## Security Enhancements

-   **Password Hashing**: Passwords are hashed using `bcrypt` with a configurable salt round (`SALT_ROUNDS`).
-   **Preventing Rainbow Table Attacks**: Salts ensure that each hashed password is unique, even for identical passwords.
-   **Validation**: Ensure input data is sanitized and validated before database insertion.
- ## Session and Cookie Management

This application uses **express-session** and **Passport.js** to maintain a secure session for authenticated users.

-   Sessions are stored server-side, and session cookies are sent to the user’s browser.
-   Passport.js serializes and deserializes the user, linking the session ID with user details.

**Configuration Details**:

-   The `SESSION_SECRET` environment variable is used to sign and verify session cookies.
-   Cookies are configured to be secure in production and expire after a specific duration.

## Future Enhancements

-   Implement session or token-based authentication for managing logged-in users.
-   Add password reset functionality with email verification.
-   Enforce strong password policies during registration.

## License

This project is licensed under the MIT License.


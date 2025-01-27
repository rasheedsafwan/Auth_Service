# Auth_Service

**Auth_Service** is an authentication and authorization service designed to manage user access within applications. It handles user registration, login, and token generation, ensuring secure and efficient access control.

---

## Features

- **User Registration**: Allows new users to create accounts securely.
- **User Login**: Authenticates users and provides access tokens.
- **Token Generation**: Issues JWT tokens for session management and API authentication.
- **Access Control**: Manages user roles and permissions to restrict unauthorized access.

---

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/rasheedsafwan/Auth_Service.git
   cd Auth_Service
   ```

2. **Build the Project**:
   Ensure you have [Gradle](https://gradle.org/) installed. Then, run:
   ```bash
   gradle build
   ```

3. **Run the Application**:
   ```bash
   gradle run
   ```

---

## Usage

After running the application, the Auth_Service will be accessible at `http://localhost:8080`. You can interact with the service using tools like [Postman](https://www.postman.com/) or [curl](https://curl.se/).

### Endpoints

- **Register**: `/api/signup`
  - Method: `POST`
  - Description: Creates a new user account.
  - Payload:
    ```json
    {
      "username": "exampleUser",
      "password": "examplePassword"
    }
    ```

- **Login**: `/api/login`
  - Method: `POST`
  - Description: Authenticates a user and returns a JWT token.
  - Payload:
    ```json
    {
      "username": "exampleUser",
      "password": "examplePassword"
    }
    ```

---

## Technologies Used

- **Java**: Core programming language.
- **Spring Boot**: Framework for building the application.
- **JWT (JSON Web Tokens)**: For secure token-based authentication.
- **Gradle**: Build automation tool.

---

## Notes for Relearning

### **JWT Authentication**
- JWT tokens are generated during login and include claims such as the username, roles, and expiration time.
- **Key Points**:
  - Tokens are signed using a secret key to ensure authenticity.
  - Always validate the token on the server for protected resources.

### **Spring Boot Security**
- Used to secure the application by configuring authentication and authorization.
- Configured to use JWT for stateless session management.
- **Helpful Classes/Annotations**:
  - `@RestController`: Used to define API endpoints.
  - `@PostMapping` and `@GetMapping`: Define HTTP endpoints.
  - `@Autowired`: Injects dependencies like services or repositories.

### **Project Setup with Gradle**
- Use Gradle to manage dependencies like Spring Boot and JWT libraries.
- Add necessary dependencies in `build.gradle`.
  ```gradle
  implementation 'org.springframework.boot:spring-boot-starter-security'
  implementation 'io.jsonwebtoken:jjwt-api:0.11.5'
  ```

### **API Design**
- REST principles were followed to create endpoints.
- Use tools like Postman to test endpoints during development.

### **Protected Resource**
- Implemented middleware to validate JWT tokens before granting access to protected endpoints.
- Example:
  - Verify the `Authorization` header contains a valid `Bearer` token.

### **Token Management**
- Generate tokens using `io.jsonwebtoken.Jwts`.
- Validate tokens by parsing them and checking the claims.
- Example Code:
  ```java
  private Claims extractAllClaims(String token) {
      return Jwts.parser()
                 .setSigningKey(secretKey)
                 .parseClaimsJws(token)
                 .getBody();
  }
  ```

---

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any enhancements or bug fixes.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

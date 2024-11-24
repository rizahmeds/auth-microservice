FastAPI User Authentication Microservice
========================================

A robust and secure user authentication microservice built with FastAPI, providing essential authentication and user management features.

Features
--------

*   **User Management**
    
    *   User registration with email and username
        
    *   Secure password hashing using bcrypt
        
    *   Email and username uniqueness validation
        
    *   User profile retrieval
        
*   **Authentication**
    
    *   JWT (JSON Web Token) based authentication
        
    *   Secure token generation and validation
        
    *   Protected routes with token verification
        
*   **Security**
    
    *   Password hashing with bcrypt
        
    *   Input validation using Pydantic
        
    *   SQL injection protection with SQLAlchemy
        
    *   JWT token expiration
        
*   **API Documentation**
    
    *   Interactive API documentation (Swagger UI)
        
    *   OpenAPI specification
        

Prerequisites
-------------

*   Python 3.8+
    
*   pip (Python package manager)
    
*   Virtual environment (recommended)
    

Installation
------------

1.  Clone the repository:
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopygit clone   cd fastapi-auth-microservice   `

1.  Create and activate a virtual environment:
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopy# Windows  python -m venv venv  .\venv\Scripts\activate  # Linux/MacOS  python3 -m venv venv  source venv/bin/activate   `

1.  Install dependencies:
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopypip install -r requirements.txt   `

1.  Create a .env file in the project root:
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   envCopyDATABASE_URL=sqlite:///./users.db  SECRET_KEY=your-secure-secret-key   `

Running the Service
-------------------

1.  Start the server:
    

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopyuvicorn main:app --reload   `

1.  The service will be available at:
    
    *   API: [http://localhost:8000](http://localhost:8000)
        
    *   Documentation: [http://localhost:8000/docs](http://localhost:8000/docs)
        
    *   OpenAPI Spec: [http://localhost:8000/openapi.json](http://localhost:8000/openapi.json)
        

API Endpoints
-------------

### Public Endpoints

*   jsonCopy{ "email": "user@example.com", "username": "user123", "password": "secure\_password"}
    
    *   Register a new user
        
    *   Required fields: email, username, password
        
*   **POST /token**
    
    *   Login and obtain access token
        
    *   Form fields: username, password
        
    *   Returns JWT token
        

### Protected Endpoints

*   **GET /users/me**
    
    *   Get current user information
        
    *   Requires Bearer token authentication
        

Usage Examples
--------------

### Register a New User

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopycurl -X POST "http://localhost:8000/register" \       -H "Content-Type: application/json" \       -d '{"email":"user@example.com","username":"user123","password":"secure_password"}'   `

### Login and Get Token

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopycurl -X POST "http://localhost:8000/token" \       -H "Content-Type: application/x-www-form-urlencoded" \       -d "username=user123&password=secure_password"   `

### Get User Profile

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopycurl -X GET "http://localhost:8000/users/me" \       -H "Authorization: Bearer your_access_token"   `

Project Structure
-----------------

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   Copy├── main.py           # FastAPI application and routes  ├── models.py         # SQLAlchemy models  ├── schemas.py        # Pydantic schemas for request/response  ├── database.py      # Database configuration  ├── auth.py          # Authentication utilities  ├── requirements.txt # Project dependencies  └── .env            # Environment variables   `

Security Considerations
-----------------------

1.  **Environment Variables**: Never commit .env file to version control
    
2.  **Secret Key**: Use a strong, unique secret key for JWT token generation
    
3.  **Password Storage**: Passwords are hashed using bcrypt before storage
    
4.  **Token Expiration**: JWT tokens expire after 30 minutes by default
    

Development
-----------

### Running Tests

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   bashCopypytest   `

### Code Style

Follow PEP 8 guidelines for Python code style.

Error Handling
--------------

The service includes comprehensive error handling for common scenarios:

*   Email already registered
    
*   Invalid credentials
    
*   Token validation failures
    
*   Database connection issues
    

Contributing
------------

1.  Fork the repository
    
2.  Create a feature branch
    
3.  Commit your changes
    
4.  Push to the branch
    
5.  Create a Pull Request
    

Future Improvements
-------------------

*   Email verification
    
*   Password reset functionality
    
*   Rate limiting
    
*   Role-based access control
    
*   OAuth2 social login integration
    
*   Refresh token implementation
    

License
-------

This project is licensed under the MIT License - see the LICENSE file for details.

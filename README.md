# KiberBank-API
The KiberBank API allows retrieval of user data based on their email from a database. This API is designed to handle POST requests and returns user information in JSON format.


### Overview

The KiberBank API allows retrieval of user data based on their email from a database. This API is designed to handle POST requests and returns user information in JSON format.

### Base URL

`bank.hoku.ge/api/bot.php`

### Endpoints

Retrieve User Data

- **URL:** `/bot.php`
- **Method:** `POST`
- **Request Parameters:**
    - `email` (required): The email of the user for which data is requested.
- **Response:**
    - Success Response:
        - HTTP Status Code: `200 OK`
        - JSON Object:
            
            ```json
            {
                "success": true,
                "message": "User data retrieved",
                "user": {
                    "email": "user@example.com",
                    "name": "John Doe",
                    "balance": 5000
                }
            }
            ```
            
    
    - Error Responses:
        - HTTP Status Code: `404 Not Found`
        - JSON Object (User not found):
            
            ```json
            {
                "success": false,
                "message": "User not found"
            }
            ```
            
        - HTTP Status Code: `400 Bad Request`
        - JSON Object (Incomplete data received or invalid request method):
            
            ```json
            {
                "success": false,
                "message": "Incomplete data received"
            }
            ```
            
        - HTTP Status Code: `500 Internal Server Error`
        - JSON Object (Connection error):
            
            ```json
            {
                "success": false,
                "message": "Connection error"
            }
            ```
            

### Usage

To retrieve user data, make a `POST` request to the endpoint URL with the `email` parameter in the request body. Ensure the `Content-Type` header is set to `application/json`.

### Example Request

```
POST /api/bot.php HTTP/1.1
Host: bank.hoku.ge
Content-Type: application/json

{
    "email": "user@example.com"
}
```

### Example Response

```json
{
    "success": true,
    "message": "User data retrieved",
    "user": {
        "email": "user@example.com",
        "name": "John Doe",
        "balance": 5000
    }
}
```

### Error Handling

- Ensure the `email` parameter is provided in the request body.
- Handle error responses based on the provided status codes and messages in the JSON response.

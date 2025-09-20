# alx-project-0x14

## API Overview
The MoviesDatabase API provides access to a wide collection of movie and TV show data. It allows developers to search for movies, retrieve details about specific titles, explore trending content, access cast and crew information, and much more. The API is designed to support integration into applications that require film-related data, including ratings, genres, images, and release information.

## Version
Current API Version: **1.0**

## Available Endpoints
- **/titles** – Retrieve a list of movies and TV shows.
- **/titles/{id}** – Get details about a specific movie or show by its ID.
- **/titles/search** – Search for movies or shows by title.
- **/titles/trending** – Fetch a list of currently trending movies and shows.
- **/actors/{id}** – Retrieve detailed information about a specific actor.
- **/genres** – List all available genres in the database.

## Request and Response Format
Requests are made over **HTTPS** and responses are returned in **JSON** format.

**Example Request:**
```http
GET https://api.moviesdatabase.com/titles/search?query=Inception
Authorization: Bearer <API_KEY>
```

**Example Response:**
```json
{
  "id": "tt1375666",
  "title": "Inception",
  "year": 2010,
  "genres": ["Action", "Sci-Fi", "Thriller"],
  "rating": 8.8,
  "cast": [
    { "id": "nm0000138", "name": "Leonardo DiCaprio" },
    { "id": "nm0330687", "name": "Joseph Gordon-Levitt" }
  ]
}
```

## Authentication
All requests require authentication using an **API key**. The API key should be passed in the request header:
```http
Authorization: Bearer <API_KEY>
```

## Error Handling
Common errors returned by the API include:
- **400 Bad Request** – Invalid request format or parameters.
- **401 Unauthorized** – Missing or invalid API key.
- **404 Not Found** – Requested resource not found.
- **500 Internal Server Error** – An issue on the server side.

When handling errors, always check the response code and the accompanying error message. Implement retries with backoff for server-side errors.

## Usage Limits and Best Practices
- The API enforces **rate limits** (e.g., 100 requests per minute). Exceeding the limit will result in a **429 Too Many Requests** error.
- Cache frequently accessed data (e.g., popular movies) to reduce API calls.
- Use pagination when retrieving large lists of movies or shows.
- Ensure secure storage of your API key and avoid exposing it in client-side code.


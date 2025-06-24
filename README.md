# JournalApp

A simple End-to-End Encrypted (E2EE) journal application built with Spring Boot and MongoDB.

## Features
- Create, read, update, and delete journal entries
- RESTful API
- MongoDB for persistent storage
- Health check endpoint

## Requirements
- Java 17+
- Maven
- MongoDB (running locally on default port 27017, or configure in `application.properties`)

## Getting Started

### 1. Clone the repository
```bash
git clone <repo-url>
cd JournalApp
```

### 2. Configure MongoDB
By default, the app connects to MongoDB at `localhost:27017` and uses the `journaldb` database. You can change this in `src/main/resources/application.properties`.

### 3. Build and Run
```bash
./mvnw spring-boot:run
```
Or build the JAR:
```bash
./mvnw clean package
java -jar target/journalApp-0.0.1-SNAPSHOT.jar
```

## API Endpoints

### Health Check
- `GET /health-check` → returns `Ok`

### Journal Entries
- `GET /journal` → List all journal entries
- `POST /journal` → Create a new journal entry
  - Body: `{ "title": "...", "content": "..." }`
- `GET /journal/id/{id}` → Get a journal entry by ID
- `PUT /journal/id/{id}` → Update a journal entry by ID
  - Body: `{ "title": "...", "content": "..." }`
- `DELETE /journal/id/{id}` → Delete a journal entry by ID

#### Example JournalEntry JSON
```json
{
  "id": "<ObjectId>",
  "title": "My Day",
  "content": "Today was great!",
  "date": "2024-04-27T12:34:56"
}
```

## Data Model
- **id**: MongoDB ObjectId
- **title**: String
- **content**: String
- **date**: LocalDateTime (set automatically on creation)

## Configuration
Edit `src/main/resources/application.properties` to change MongoDB host, port, or database name. Example:
```
spring.data.mongodb.host=localhost
spring.data.mongodb.port=27017
spring.data.mongodb.database=journaldb
```

## Testing
Run tests with:
```bash
./mvnw test
```

## License
This project is for educational/demo purposes.

```mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: clicks 'Save' button
    activate browser
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTTP status code 302 (URL redirect)
    deactivate server

    Note right of browser: The server asks the browser to do a new HTTP GET to /exampleapp/notes
    Note left of browser: The browser reloads the Notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the Javascript file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "Test", "date": "2024-03-24" }, ... ]
    deactivate server

    Note left of browser: The browser executes the callback function that renders the notes

    ```
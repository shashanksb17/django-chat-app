# [Django Chat Application](https://django-chat-application.onrender.com)

The Django Chat Application is a web-based platform that allows users to engage in real-time chat conversations with their friends, manage their profiles, send and accept friend requests, and search for other users within the application. This project provides a user-friendly interface for communication and social interaction, utilizing API calls and polling for real-time chat updates.

## Key Features

- **User Authentication**: Users must first log in to access the application. New users have the option to sign up for an account.

- **User Profiles**: Each user has a profile page displaying their information. Users can edit their profile information.

- **Navigation**: The application features a simple UI with the following buttons: "Edit Profile," "Logout," and "Search" to allow users to find other users on the platform.

- **Friend Management**: Users can maintain two lists: "Friend List" and "Request List." Users can click on friend names in these lists to access profiles or start chats.

- **Chatting**: Users can initiate chat conversations by clicking on a friend's name. Real-time chat functionality is implemented using API calls and polling, enabling near-instant communication.

- **Friend Requests**: Users can send friend requests to others by visiting their profiles. Pending friend requests can be accepted or rejected. Accepted requests add users to each other's friend lists.

- **Friend Profile Options**: Users can perform actions on friends' profiles, including "Remove Friend" and "Chat."

## User Flow

1. User logs in or signs up.
2. On the dashboard, the user can:
   - Edit their profile information.
   - Log out of their account.
   - Search for other users.
   - View their friend list and pending friend requests.
3. In the friend list and request list:
   - Clicking on a friend's name opens a chat with them.
   - Clicking on a pending request opens the requester's profile.
   - Pending requests can be accepted or rejected.
4. In a friend's profile:
   - The user can choose to remove the friend or start a chat.

## Technology Stack

- Django (Python web framework)
- Front-end technologies for the UI (HTML, CSS, JavaScript)
- API calls and polling for real-time chat updates
- Database for user information and chat history (e.g., PostgreSQL)

## Project Goals

- Create a user-friendly and interactive chat application.
- Implement secure user authentication and authorization.
- Provide a smooth and responsive user interface.
- Enable real-time chat features using API calls and polling.
- Develop a robust friend management system with friend requests.

## Future Enhancements

- Implement notifications for friend requests and new messages.
- Add multimedia support (e.g., file sharing, image uploads).
- Enhance user profiles with profile pictures and additional details.
- Implement group chats and chat rooms.

## Getting Started

To get started with the Django Chat Application, follow these steps:

1. Clone the repository to your local machine:

   ```bash
   git clone https://github.com/devnamdev2003/django-chat-app.git
   ```

2. Create a virtual environment and install the project dependencies:

   ```bash
   cd django-chat-app
   python -m venv venv
   source venv/bin/activate  # On Windows, use: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. Set up the database:

   ```bash
   python manage.py migrate
   ```

4. Start the development server:

   ```bash
   python manage.py runserver
   ```

5. Open a web browser and navigate to `http://localhost:8000/` to access the application.

## Docker Deployment

To deploy the Django Chat Application using Docker, follow these steps:

1. Ensure you have Docker and Docker Compose installed on your machine.

2. Create a `Dockerfile` in the root of your project directory:

   ```Dockerfile
   # Use the official Python image as a base image
   FROM python:3.10-slim

   # Set environment variables
   ENV PYTHONDONTWRITEBYTECODE=1
   ENV PYTHONUNBUFFERED=1

   # Set work directory
   WORKDIR /app

   # Install dependencies
   COPY requirements.txt /app/
   RUN pip install --upgrade pip && pip install -r requirements.txt

   # Copy project
   COPY . /app/

   # Expose port 8000
   EXPOSE 8000

   # Run the application
   CMD ["gunicorn", "--bind", "0.0.0.0:8000", "registration.wsgi:application"]
   ```

3. Create a `docker-compose.yml` file in the root of your project directory:

   ```yaml
   version: '3'

   services:
     web:
       build: .
       command: gunicorn --bind 0.0.0.0:8000 registration.wsgi:application
       ports:
         - "8000:8000"
       volumes:
         - .:/app
       environment:
         - DEBUG=1
   ```

4. Build and run your Docker containers:

   ```bash
   docker-compose up --build
   ```

5. Open a web browser and navigate to `http://localhost:8000/` to access the application.

## Contributions

We welcome contributions from the community! If you'd like to contribute to the project, please follow these guidelines:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them with clear, descriptive commit messages.
4. Push your branch to your fork.
5. Create a pull request to merge your changes into the main project.

## License

This project is licensed under the [MIT License](LICENSE).

## Images

Here are some screenshots from the Django Chat Application:

**Login Page:**

![Login](https://filesstatic.netlify.app/Chatapp/img/login.png)

**Signup Page:**

![Signup](https://filesstatic.netlify.app/Chatapp/img/signup.png)

**Chat Interface:**

![Chat Interface](https://filesstatic.netlify.app/Chatapp/img/chat.png)

**Friend Management:**

![Friend Management](https://filesstatic.netlify.app/Chatapp/img/interface.png)

**Search Friends**

![Search Page](https://filesstatic.netlify.app/Chatapp/img/search.png)

**Edit Profile**

![Edit Profile](https://filesstatic.netlify.app/Chatapp/img/edit.png)

**Profile**

![Profile](https://filesstatic.netlify.app/Chatapp/img/user.png)


 User Manual Procedure: Setting Up a GitHub Repository and Making a First Commit
This guide explains how to set up a GitHub repository from scratch and upload your first project files. It is written for a first-semester computing student who has basic computer skills but may not have used Git or GitHub before.
Git is a tool that helps developers keep track of changes made to their files. GitHub is an online platform where those files and projects can be stored and shared.
Prerequisites
Before starting, make sure you have:
A computer with Windows, macOS, or Linux.
A stable internet connection.
A GitHub account.
Git installed on your computer.
A terminal or command prompt.
A text editor or code editor, such as Visual Studio Code.
Basic knowledge of creating and saving files.
Step-by-Step Procedure
Open your web browser and sign in to your GitHub account.
Expected result: Your GitHub dashboard should appear.
Click the “+” button and select “New repository.”
Expected result: The page for creating a new repository should open.
Enter a name for your repository.
Expected result: The repository name should appear in the name field.
Select whether the repository will be Public or Private.
Expected result: Your chosen visibility option should be selected.
Click the “Create repository” button.
Expected result: GitHub should create the repository and display its main page.
Open the terminal or command prompt on your computer.
Expected result: A command-line window should be ready for you to enter commands.
Navigate to the location where you want to store your project.
Expected result: The terminal should show that you are in the correct folder.
Create a new project folder using the mkdir command.
Expected result: A new folder should be created.
Move into the new project folder using the cd command.
Expected result: The project folder should become your current working directory.
Run the git init command.
Expected result: Git should initialize a new local repository in the folder.
Create a file inside the project folder.
Expected result: A new project file should exist in the folder.
Save the file.
Expected result: The file should be stored successfully in the project folder.
Run the git status command.
Expected result: Git should show the new file as an untracked file.
Run git add ..
Expected result: The file should be added to the staging area.
Run git status again.
Expected result: The file should appear as ready to be committed.
Run git commit -m "Initial commit".
Expected result: Git should create your first commit and save the current version of your project.
Copy the repository URL from the GitHub repository page.
Expected result: You should have the repository address needed to connect your local project to GitHub.
Run git remote add origin REPOSITORY_URL.
Expected result: Your local repository should be connected to the GitHub repository.
Run git branch -M main.
Expected result: The main branch should be named main.
Run git push -u origin main.
Expected result: Your first commit should be uploaded to GitHub.
Refresh the GitHub repository page.
Expected result: Your project files and the message “Initial commit” should be visible online.
Screenshot Description
I would include a screenshot of the GitHub repository after the first commit has been uploaded successfully. The screenshot should show the repository name, the main branch, the project file, and the “Initial commit” message. This would show that the local project was successfully connected to GitHub and uploaded.
Troubleshooting Note
Common Error: git is not recognized as a command
A common problem for beginners is seeing an error such as “git is not recognized as an internal or external command” or “git: command not found.” This normally means that Git has not been installed correctly or that the terminal cannot locate the Git installation.
To fix this problem, make sure Git is installed and then close and reopen your terminal. You can check whether Git is installed by running:
git --version
Expected result: The terminal should display the installed version of Git.

B) API Reference Entry: Create a New Task
Create Task
HTTP Method and Endpoint
Method: POST
Endpoint Path: /api/v1/projects/{projectId}/tasks
Description
This endpoint allows an authenticated user to create a new task in a project management application. The user sends information about the task, including its title, optional description, assigned user, due date, and priority.
When the request is successful, the application creates the task and returns the details of the new task.
Request Parameters
Path Parameters
Name
Data Type
Required
Description
projectId
Integer
Yes
The unique ID of the project where the task will be created.

Query Parameters
This endpoint does not use any query parameters.
Request Body Parameters
Name
Data Type
Required
Description
title
String
Yes
The name or title of the task.
description
String
No
Extra details about what the task involves.
assigneeId
Integer
Yes
The unique ID of the user assigned to the task.
dueDate
String
Yes
The date by which the task should be completed, using YYYY-MM-DD format.
priority
String
Yes
The priority of the task. Accepted values are low, medium, and high.

Required Request Headers
Header
Required
Description
Authorization
Yes
Contains the user's authentication token in the format Bearer <token>.
Content-Type
Yes
Specifies that the request body contains JSON data. The value must be application/json.
Accept
Yes
Specifies that the client expects a JSON response. The value must be application/json.

Authentication Example
Authorization: Bearer your_access_token_here
Example Request Body
{
  "title": "Complete the login page design",
  "description": "Create a simple and user-friendly design for the application's login page.",
  "assigneeId": 42,
  "dueDate": "2026-09-05",
  "priority": "high"
}
HTTP Response Codes
201 Created
The task was created successfully. The response contains the details of the newly created task.
400 Bad Request
The request contains invalid or incomplete information. For example, a required field may be missing, the due date may have an incorrect format, or the priority value may not be valid.
401 Unauthorized
The request does not contain a valid authentication token, or the user is not logged in.
403 Forbidden
The user is authenticated but does not have permission to create a task in the specified project.
404 Not Found
The project with the given projectId does not exist or cannot be found.
409 Conflict
The request conflicts with an existing resource or application rule, such as attempting to create a duplicate task when duplicates are not allowed.
500 Internal Server Error
An unexpected problem occurred on the server while processing the request.
Example Successful Response
Status: 201 Created
{
  "id": 1258,
  "projectId": 101,
  "title": "Complete the login page design",
  "description": "Create a simple and user-friendly design for the application's login page.",
  "assignee": {
    "id": 42,
    "name": "Jane Doe"
  },
  "dueDate": "2026-09-05",
  "priority": "high",
  "status": "open",
  "createdAt": "2026-08-24T13:04:00Z",
  "createdBy": {
    "id": 15,
    "name": "Ohuro"
  }
}
Response Field Description
Field
Data Type
Description
id
Integer
The unique ID assigned to the new task.
projectId
Integer
The ID of the project containing the task.
title
String
The title of the task.
description
String
Additional information about the task.
assignee
Object
Information about the user assigned to the task.
dueDate
String
The task's due date.
priority
String
The priority level of the task.
status
String
The current status of the task.
createdAt
String
The date and time when the task was created.
createdBy
Object
Information about the authenticated user who created the task.

Conclusion
The first section provides a simple guide for creating a GitHub repository and making a first commit. The second section demonstrates how professional API documentation can describe an endpoint clearly, including its request requirements, authentication, possible responses, and example data.


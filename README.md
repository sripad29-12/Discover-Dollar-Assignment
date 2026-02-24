Here is the step by step process for setting up, containerizing the MEAN Stack application.

Step-1: Setting up the code in the local machine and pushing to remote repo.

- Create a remote git repository.
- Push the code to the remote repo from local repo and check it properly.

Step 2: Containerizing the MEAN stack application.

- Create two separate docker files for both frontend and backend respectively inside their folders.
- Build the images and push them to dockerhub one after the other.
- Test the containers locally
- After successful testing, commit the changes and push the changes to remote repo.

Step-3: Creating the Virtual Machine and deploying the application using docker-compose.

- Use whatever vm you want from the favourable CSP. 
- I am using AWS EC2 ubuntu, t2.micro instance.
- Install docker on the instance and give the necessary permissions and restart the instance.
- Create a docker-compose file on your local repo with the necessary steps and also use official MongoDB image inside the file for backend and db connection.
- Commit and push the changes to remote git repo and clone the project into the instance.
- You can now access the app with the specified ports.

Step-4 Creating a CICD pipeline for auto building and deployment of docker images.

- Set up Github actions CICD for this.
- Create a .github/workflows/cicd.yml inside the project folder.
- Write the appropriate workflow like, building backend image, frontend image, push to the dockerhub.
- Create the github-action-key with key generations and configure the private and public keys for the github secrets and vm respectively and link the secrets with the instance.
- write the workflow for pulling the images and starting and running the latest images from the registry with every change in the commit and reflecting the change inside the instance through docker-compose.

Step-5 Creating Nginx reverse proxy:

- To make the app accessible through the single port (80), create an nginx folder inside the project.
- Write the workflow and map the routes.
- Make necessary changes inside docker-compose.yml to map the port.
- The application is now accessible on the single port.

<img width="1877" height="807" alt="Screenshot 2026-02-24 152111" src="https://github.com/user-attachments/assets/55a189a8-54bf-4758-8a16-e961341db5ee" />

<img width="1851" height="577" alt="deploy 1" src="https://github.com/user-attachments/assets/5e0477e6-7aa2-4651-af48-8334651b97fc" />

<img width="1839" height="781" alt="Screenshot 2026-02-24 152358" src="https://github.com/user-attachments/assets/5489c271-4780-40d5-a956-34db8e17d079" />

<img width="1800" height="407" alt="deploy3" src="https://github.com/user-attachments/assets/aef6621d-e45b-478b-850f-7774b5be0227" />

<img width="1890" height="808" alt="ui1" src="https://github.com/user-attachments/assets/455a2c97-ac73-4ce9-8e6a-e9ffca5c343c" />

<img width="1886" height="692" alt="Screenshot 2026-02-24 152621" src="https://github.com/user-attachments/assets/4daf74bd-f001-40a8-9dbf-0f219f9df879" />






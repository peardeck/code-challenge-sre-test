# code-challenge-sre-test

This is the SRE technical challenge for Pear Deck. Read this README.md for instructions on guidelines and the task to solve.

# Rules

At GoGuardian, our Pear Deck engineering team values the ability to think through a project methodically, solve problems creatively, balance simplicity with innovation, write clear code that is easy to read and understand, follow sustainable standards and accepted best practices, make well reasoned decisions, and learn and grow through your work.

We've developed this code challenge to allow you, as a candidate, to showcase these abilities through executing a standard piece of work that touches on all of the core competencies of a Site Reliability Engineer.

## Logistics

- Please read the exercise in full before planning and beginning your work
- You are welcome to reach out to ask any questions, gain clarification, or gather requirements at any time

## Execution

- We ask that you execute the challenge in `Terraform`, `Helm`, and `git` as it most closely reflects the work you will do on the Pear Deck SRE team at GoGuardian. If you choose to use any scripting/programming languages to glue everything together, feel free to use what you are most comfortable with, though keep in mind that we often use `Python` for a lot of our own glue code.
- Your work metholodogy is shown through your commit history, so please consider this in your work
- Comments and documentation to mark your decisions, explain your solutions, and show your reasoning are expected.

## Timing

- You will have one week from the time you receive the challenge to complete and return your work.
- We ask that you try to spend three hours or less on your solution within that week.

## Delivery

- Please return your solution as a zipfile or tarball of your git repo according to the instructions of the recruiter

## Review

- After you deliver your work, one of our engineers will review your work
- Should you pass and move onto team interviews with our engineering team, there will likely be questions or discussions relating to this work, so please be prepared to help explain/teach your work!

# How this challenge will be judged

- First and foremost, your ability to develop a working solution using the tech stack specified in the rules
- Your execution of coding best practices and readability of your code
- Source control and work methodology is *important* so please use git, use meaningful commit messages and organize your work accordingly
- There is not one *correct* solution and so your solution will be unique. We will be paying attention to how you decide to solve the challenge, so please ensure that it reflects your strengths
- Explaining your thinking, decision points, and solution are critical. Comments and documentation will be reviewed and should provide context and clarity around your completed code.

# The Task

You will be provided with a static Google JSON authentication key for using `gcloud` and Terraform commands. No need for shared Terraform state - please commit your state file alongside your Terraform code if you opt to use Terraform.

Your task is to:

- Serve a basic HTTP response with a load balancer. We use GKE so you can elect to use an ingress controller or a simple HTTP `LoadBalancer` service. Use `strm/helloworld-http` (https://hub.docker.com/r/strm/helloworld-http) as your HTTP server - no need to modify the image or anything.
  - You might need to debug any problems that occur while trying to have this serve traffic. Document any fixes required in either a separate text file or alongside your code.
- Ensure that the `Deployment` is secure with a custom service account with no Kubernetes permissions.
- Set up a `CronJob` that outputs "Hello World" every thirty minutes.
- Create a GCS bucket, `peardeck-sre-challenge-<first_initial><last_name>` (either with Terraform or GKE Config Connector.) For example, if your name is John Doe, create a GCS bucket `peardeck-sre-challenge-jdoe`.

Optional tasks:

- Document exactly what else you'd add to best monitor the service. Even though the HTTP server is a toy service, explain what sort of basic things you'd want to monitor as if it was a production service. (No need to implement an actual solution here.)
- Imagine that the service is stateful: what considerations would you keep in mind while designing out the service? Document what these considerations would be and what informed your decision. (No need to implement an actual solution here.)

## Stack preferences

- Helm 3.x
- Terraform 1.x
- Google Kubernetes Engine (assume that GKE Config Connector is enabled)

## Folder structure

- The `helm/` folder contains a skeleton Helm chart.
- The `terraform/` folder contains a blank Terraform workspace to use.

## Setup

1. Ensure you have `git` installed on your computer
2. Ensure that you have the Terraform, `kubectl`, `helm`, and `gcloud` CLIs installed.
3. Follow instructions below to authenticate against the Kubernetes cluster:
  - Run `gcloud container clusters get-credentials pd-us-sre-code-challenge-cluster --project pd-us-sre-code-challenge-cluster --zone us-central1-f`
  - Run `kubectl get pods` to verify connectivity 

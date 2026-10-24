# Pace demo

A simple Hello World page for practicing Git and Docker.

## Run with Docker Compose

```sh
docker compose up --build
```

Open [http://localhost:8080](http://localhost:8080). Stop the app with `Ctrl+C`; run `docker compose down` to remove its container.

The GitHub Actions workflow runs only on pushes to `main`. It lints YAML, then builds the Docker image and publishes `latest` and commit-SHA tags to Docker Hub.

To enable publishing, create a Docker Hub repository named `demo-task-board` and add these repository secrets in GitHub under **Settings → Secrets and variables → Actions**:

- `DOCKERHUB_USERNAME`: your Docker Hub username
- `DOCKERHUB_TOKEN`: a Docker Hub access token with read/write permissions

To pull and run the published image, set your Docker Hub username and start Compose:

```sh
export DOCKERHUB_USERNAME=your-dockerhub-username
docker compose up
```

Compose pulls the `latest` image; it does not build locally. To build from source instead, use `docker compose build` first.
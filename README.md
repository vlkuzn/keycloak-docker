# Keycloak Docker Setup

This repository contains a Docker setup for running Keycloak with PostgreSQL and Nginx reverse proxy.

## Prerequisites

- Docker
- Docker Compose

## Setup

1. Clone this repository:
```bash
git clone https://github.com/vlkuzn/keycloak-docker.git
cd keycloak-docker
```

2. Create SSL certificates for HTTPS:
```bash
# Generate self-signed certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout certs/key.pem \
  -out certs/cert.pem \
  -subj "/CN=keycloak.example.com"
```

3. Create your `.env` file from the example:
```bash
cp .env.example .env
```

4. Update the `.env` file with your settings:
- Change passwords
- Update hostname
- Adjust other settings as needed

5. Start the services:
```bash
docker compose up -d
```

## Access Keycloak

Once everything is running:

1. Access the Keycloak admin console at: `https://your-domain/admin`
2. Login with the credentials specified in your `.env` file:
   - Username: The value of `KC_BOOTSTRAP_ADMIN_USERNAME`
   - Password: The value of `KC_BOOTSTRAP_ADMIN_PASSWORD`

## Components

- Keycloak 26.2
- PostgreSQL 16
- Nginx 1.28.0 (Alpine)

# Dockerfile located in /var/lib/jenkins/workspace/nodejs_step2/build

ARG ARCH=
ARG IMAGE_BASE=16-alpine

FROM ${ARCH}node:$IMAGE_BASE
LABEL Name="Node.js Demo App" Version=4.8.5
LABEL org.opencontainers.image.source="https://github.com/benc-uk/nodejs-demoapp"

ENV NODE_ENV production
WORKDIR /app 

# Copy package.json and package-lock.json first for caching
COPY /src/package*.json ./
RUN npm install --production --silent

# Copy the rest of the project files to the workdir
COPY src/. .


# Expose the application port (3000 for the Express server)
EXPOSE 3000

# Start the application
ENTRYPOINT ["npm", "start"]

FROM node:22-bullseye-slim

# Set the working directory in the container
WORKDIR /app

# Copy package.json and yarn.lock
COPY package.json yarn.lock /app/

# Set the environment variable to skip Puppeteer download
ENV PUPPETEER_SKIP_DOWNLOAD=true

# Install dependencies
RUN yarn install

# Copy the current directory contents into the container at /app
COPY ./ /app/

# Build the application
RUN yarn build

# Install a static server
RUN yarn global add serve

# Expose port 5173 to access the server
EXPOSE 5173

# Command to run the application using serve
CMD ["serve", "-s", "dist", "-l", "5173"]

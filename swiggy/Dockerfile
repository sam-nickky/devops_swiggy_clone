# Stage 1: Build the React app
FROM node:16 as builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Stage 2: Serve the app with NGINX
FROM nginx:stable-alpine

# Copy built app from builder
COPY --from=builder /app/build /usr/share/nginx/html

# Copy custom NGINX config if needed
# COPY nginx.conf /etc/nginx/nginx.conf

# Expose the port NGINX will listen on
EXPOSE 80

# Start NGINX
CMD ["nginx", "-g", "daemon off;"]


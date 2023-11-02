FROM node:18-slim AS build
COPY . /home/app/
RUN npm install -g @angular/cli@16
WORKDIR /home/app/
RUN npm install && npm run build

FROM nginx:stable-alpine-slim
COPY --from=build /home/app/dist/sgcmapp/ /usr/share/nginx/html
COPY --from=build /home/app/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80

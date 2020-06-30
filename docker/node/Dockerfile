FROM node:12.14.0-alpine

RUN apk update && \
  apk add git && \
  apk add --no-cache curl && \
  curl -o- -L https://yarnpkg.com/install.sh | sh

ENV PATH $HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH

WORKDIR /app
# https://stackoverflow.com/a/32785014/232619
COPY . /app
RUN npm install
COPY ./docker/wait-for-it.sh /usr/local
RUN chmod +x /usr/local/wait-for-it.sh

EXPOSE 3000

CMD ["npm", "start"]
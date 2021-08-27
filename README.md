# WRIGHT PARTNERS STRAPI BACKEND

A REST API for Wright Partners website using Strapi (frame work cms) and Postgres for Database.

The entire routes is contained within the api folder.

## Install
 Install all dependencies :

    npm i install

## Run the app

    npm run develop

## Run the tests

    ./run-tests.sh

## Deploy the app using Heroku

- Login Heroku :
```
heroku login
```

- install Postgres Database :
```
npm i pg pg-connection-string
```

- create a `./config/env/production/database.js` file containing the folowing code :
```js
const { parse } = require("pg-connection-string");

module.exports = ({ env }) => {
  const { host, port, database, user, password } = parse(env("DATABASE_URL"));

  return {
    defaultConnection: "default",
    connections: {
      default: {
        connector: "bookshelf",
        settings: {
          client: "postgres",
          host,
          port,
          database,
          username: user,
          password,
          ssl: { rejectUnauthorized: false }
        },
        options: {
          ssl: false
        },
      },
    },
  };
};

```

- init the Git Repository : 
```
git init
heroku git:remote -a NAME_OF_HEROKU_APP
git add .
git commit -am "Initial commit"
```

- Heroku Create
```
heroku create
```

- Postgres addon
```
heroku addons:create heroku-postgresql:hobby-dev --app NAME_OF_HEROKU_APP
```

- Deploy to Heroku
```
git push heroku master
```  

# REST API

The REST API to the example app is described below.

## A. REST API For Each Page

List of pages API :
  - Global : `/global`
  - Home Page : `/hompage`
  - Philosophy Page : `/phylosophy`
  - Team Page: `/team`
  - Contact Page: `/contact-us`
  - Career Page: `/career`
  - Career Detail Page: `/career/:jobId/country/:countryId`
  - Venture Building Page : `/venture-building`
  - Cvc as Service Page : `/cvc-as-service`
  - Alumni Page: `/alumni-page`

  ## B. REST API for collections

  List of Collections : 
  - Founders : `/founders`
  - Advisories : `/advisories`
  - Squandrons : `/squadrons`
  - Offices: `/office-addresses`
  - Venture Partners: `/venture-partners`
  - Contacts: `/contacts`
  - applicants : `/applicants`
  - Alumni : `/alumni`
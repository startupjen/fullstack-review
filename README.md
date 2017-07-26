# GitHub Fetcher: Fullstack Exercise

You are given a skeleton of frontend and backend code. On the frontend, you have react. On the backend, you have express and mongo.

Your task is to fetch data from an API, store that data in a database, and display it on your app's index page.

### Takeaways

The primary purpose of this sprint is to give you the opportunity to compose together all the isolated concepts you've learned in the past 5 weeks; that's why this is an **exercise**, not an assessment. It'll be the first time you build a full-stack app from near-scratch.

## Getting Started

To install MongoDB, follow the [installation instructions](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/#install-mongodb-community-edition-with-homebrew).

Then, npm install. This repo uses webpack, so you may need to globally install webpack as well. Don't worry too much about webpack right now - it's a replacement for the babel command you used in recastly. 

```bash
$ npm install
```

And in separate terminal tabs:
```bash
$ npm run react-dev
$ npm run server-dev
$ npm run db-start
```

This repo uses webpack - don't worry about it too much, but 

Tip: See the **tips** section before you start writing any code.

## Overview

You are building an app that takes data from GitHub's API and stores it in your database. Here is an overview of what you'll need to do:

- When a user types in a **GitHub username** and submits the form, your app should:
  - Send a POST request to your express server
  - Your server should GET that user's repos from GitHub's API
  - Your server should then save the repos to the database

- When a user visits / refreshes your page, your app should:
  - GET the top (how will you determine top?) 25 repos in your express server's database
  - Take those repos and display them on the page

## Basic Requirements:

- [ ] Draw a diagram showing how this app works. Make sure your diagram includes the client, the server, and the database. 

- [ ] Explain your diagram to a fellow student, and then to a Tech Mentor or HIR.

- [ ] Design (draw a schema) a `repos` mongoose schema. You can look at `data.json` to see the structure of the data from the github api. What properties will you need? Once you've figured out your schema, complete the Repos schema in `database/index.js`, using the [Mongoose Quick Start Guide](http://mongoosejs.com/docs/index.html) for help.

- [ ] Explain your schema to a fellow student, and then to a Tech Mentor or HIR.

- [ ] When a user types a github username into the text field, use jQuery's ajax method to send a POST request to /repos/import (you'll have to fix the bug in the Search Component first).

- [ ] Complete the `/repos/import` route on your express server - in this route, you'll use the npm request library to fetch that user's Github repositories from the [Github API](https://developer.github.com/v3/).

- [ ] Store the data from the Github API in the mongo database.
    - [ ] Ensure there are no duplicate repos. If you happen to import the same repo twice, it should only show up once in your database. See the tips section about considering unique columns.

- [ ] Write a `GET /repos` endpoint that retrieves the top 25 repos stored in your database, sorted by the criteria you decided on earlier.

- [ ] Refactor the client so that when the page loads, the top 25 repos are displayed on the page.  

- [ ] Make each repo's name in the table link to that repo's page on GitHub.

- After entering a github handle in the form, update the page with the latest top 25 **without requiring a page refresh**.
  - Make sure there are no duplicates.

- [ ] Complete [Getting Started with NodeJS on Heroku](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction)

- [ ] After completing all of the above requirements, demo your app to a Tech Mentor or HIR.

**DO NOT MOVE ON TO ADANCED CONTENT UNTIL YOU HAVE DEMOED YOUR APP!**

## Advanced Content

- After an import, display a "X new repos imported, Y repos updated" message.
  - This will require the server to send back this information in the POST response.

Add the following additional components:

- When importing a repo, store the contributors for each repo as well. This will require at least one more table.
- A users component that lists all the users in your database
  - Each user's username should be a link that takes you to that user's page (see next bullet)
- A user component that displays that user's top 10 repos (in your database)
  - Each repo should be linked to its respective page on GitHub.com
  - Display a "friends list", where each friend is a contributor of any of the user's repos.

- Deploy your application on Heroku

- Refactor your database code to use a SQL database


## Tips

- DO NOT reference any code in your past projects. Instead, use google as your primary source of information.

```
Example: "How do I insert add a route in express?"

Solution:
  1. Google the above question
  2. Prioritize official docs
    – In this case, express docs
    - Do a search (command + f) on the docs page and search for your subject (routes)
    - Read
  3. If official docs are too obscure, look for a stack overflow question
     (from the google page you brought up earlier)
  4. Read the question content and make sure it's relevant
  5. If you find a good answer:
    - Understand it conceptually
    - Reference the official documentation to see if the official documentation usage matches the stack overflow answer
    - Use that information to proceed in writing your app
```

- You should learn how to be autonomous on the "how to do" (see previous bullet). However, if you don’t know “what to do", you should open a help ticket pretty quick.

  - It’ll be the same on the job. Your co-workers won’t have time to go over every "how to do" question you might have, but they will always be willing to go over the “what to do” strategies and approaches.

- The GitHub API endpoint you need to fetch from is a public endpoint, so you won't need any API keys (unless you make too many requests in one day. In that case you'll need to create and use a [personal access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)).

- To avoid duplicate repos, you first must decide which column(s) you should use to determine uniqueness. 

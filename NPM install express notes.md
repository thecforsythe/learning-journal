- go to terminal
- cd to respo
- npm init => creates package.json file
- npm install express --save => creates json in package.json? also creates package-lock.json
- npm install body-parser => installs, not sure what this does
- go to .gitignore, at bottom type: node_modules/
- in package.json include "main":"server.js"   and   "start":"node server.js",
  place server.js, package.json, package-lock.json in root directory.

- remember console.log messages from node appear in terminal
- you may also need to run live server at the same time, especially if you want json data to load into webpage. 

- include the following in server.js:
console.log('chuck\'s computer is loading express')

const express = require('express');
const app = express();
//const bodyParser = require('body-parser)').urlencode({estended: true});
const PORT = process.env.PORT || 3000;
app.use(express.static('/portfolio'));

//was unsure how to enable bodyParser since I do not have a form or articles, I have read that it may be required to parse json data. Is that correct?
/*app.post('/articles', bodyParser, function(request, response) {
// REVIEW: This route will receive a new article from the form page, new.html,
// and log that form data to the console. We will wire this up soon to actually
// write a record to our persistence layer!
console.log(request.body);
response.send('Record posted to server!!');*/

app.get('*',function(request,response) {
response.status(404).sendFile('404.html', {root: '/portfolio'});
});

app.listen(PORT, function() {
console.log('Express is listening to radio CHUCK on port ' + PORT);
});
//console.log(bodyParser)

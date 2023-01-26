# Hiru News

const request = require('request');
let previousResponse;

const checkAPI = () => {
  request('apikey', (error, response, body) => {
    if (!error && response.statusCode === 200) {
      if (previousResponse !== body) {
        console.log(body);
        previousResponse = body;
      }
    } else {
      console.log(`Error: ${error}`);
      console.log(`Status code: ${response.statusCode}`);
    }
  });
}

setInterval(checkAPI, 60000); // check the API every minute (60000 milliseconds)

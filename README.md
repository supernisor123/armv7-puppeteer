# armv7/docker-puppeter
DockerHub:https://hub.docker.com/r/supernisor/armv7-puppeteer
The docker image is for container to run puppeteer instantly .
This is for the docker run script using puppeteer with current version:
  - Base Image : ubuntu 16.04 for armv7
  - Chromium-browser 74.0.3729
  - NodeJs : 10.14.0 
  - puppeteeer : 1.10.0

```
//make sure the current core is based on armv7 
uname -a 
```

 # How to Use 

  - Build by this DockerFile or pull the image
  
  ```sh
  docker pull supernisor/armv7-puppeteer
  ```
  - Add executablePath:'/usr/bin/chromium-browser'
  - using the base commands  :
  ```sh 
  docker run -i -t -v "script path:/home/pptruser/path" docker-puppeter:1.10.0 node example.js 
  ```

### example.js 
```
const puppeteer = require('puppeteer');

(async() => {
    const browser = await puppeteer.launch({
        executablePath:'/usr/bin/chromium-browser',
        args: [
            '--no-sandbox',
            '--disable-setuid-sandbox'
        ]
    });
    const page = await browser.newPage();
    await page.goto('https://www.google.com/', {waitUntil: 'networkidle2'});
    browser.close();
})();
```


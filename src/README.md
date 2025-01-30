# Problems

## Problem

inside the `markdownload/src` folder, I want to build the  extension with `npm run build`, following error appears:

``` bash
sh: 1: web-ext: not found
```

## Solution

It looks like the `web-ext` command is not found. This usually happens if the `web-ext` package is not installed globally or locally in your project. Here are the steps to resolve this issue:

1. **Install `web-ext` locally**:
   Run the following command to install `web-ext` as a local dependency in your project:
   
```sh
   npm install web-ext --save-dev
   ```
2. **Update your `package.json` scripts**:
   Modify your `package.json` scripts to use the locally installed `web-ext` by prefixing the command with `npx`. This ensures that the locally installed version is used.

   Here is the updated `package.json`:
   
```json
   {
     "scripts": {
       "npminstall": "npm install",
       "build": "npx web-ext build",
       "start:firefoxdeveloper": "npx web-ext run -f firefoxdeveloperedition -u https://en.wikipedia.org/wiki/Special:Random --bc",
       "start:chromedevwin": "npx web-ext run -t chromium --chromium-binary \"C:\\Program Files\\Google\\Chrome Dev\\Application\\chrome.exe\" -u https://en.wikipedia.org/wiki/Special:Random --bc",
       "start:waveboxwin": "npx web-ext run -t chromium --chromium-binary %localappdata%/WaveboxApp/Application/wavebox.exe",
       "start:androidwin11": "adb connect 127.0.0.1:58526 && npx web-ext run -t firefox-android --adb-device 127.0.0.1:58526 --firefox-apk org.mozilla.fenix"
     },
     "devDependencies": {
       "web-ext": "^7.4.0"
     }
   }
   ```
3. **Run your script again**:
   Now, try running your script again. For example:
   
```sh
   npm run build
   ```
This should resolve the issue with the `web-ext` command not being found.

------

- 
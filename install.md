执行 sudo npm run install-linux
https://github.com/electron/electron/issues/21251
ELECTRON_MIRROR="https://cdn.npm.taobao.org/dist/electron/"
npm config set ELECTRON_MIRROR http://npm.taobao.org/mirrors/electron/

electron


1.选择项目文件夹
2.npm init
3.npm install electron --save-dev
4.npm --registry=https://registry.npm.taobao.org install
5.node install.js的时候ctrl+c取消,y确定
6.cd ./node_modules/electron
7.下载https://cdn.npm.taobao.org/dist/electron/7.0.0/electron-v7.0.0-win32-x64.zip并复制到上面的文件夹,重命名为electron.zip
此为64位win版本,如果是其他版本请进入https://cdn.npm.taobao.org/dist/electron/7.0.0页面选择下载
8.修改 ./node_modules/electron/install.js,如下:
```shell script
#!/usr/bin/env node

const version = require('./package').version

const fs = require('fs')
const os = require('os')
const path = require('path')
const extract = require('extract-zip')
const platformPath = 'electron.exe'
const zipPath = "./electron.zip"
extractFile (zipPath)
// unzips and makes path.txt point at the correct executable
function extractFile (zipPath) {
  extract(zipPath, { dir: path.join(__dirname, 'dist') }, function (err) {
    if (err) return onerror(err)
    fs.writeFile(path.join(__dirname, 'path.txt'), platformPath, function (err) {
      if (err) return onerror(err)
    })
  })
}
```

9../node_modules/electron目录下运行,node install.js
10.返回项目目录,安装完成,如果为github下的demo,可以在此运行npm start测试.


socks5_proxy=socks5://127.0.0.1:8080 npm i electron@12.0.13 -S

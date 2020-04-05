# Selenium UI testing with AWS Lambda Layers

This is an example of set up Selenium testing with AWS lambda layers Python3.6

### File Structure

- seleniumLayer -  Selenium
- lambda

```bash
── /seleniumLayer/  # lambda layers
  ├── /selenium  lambda layer of selenium lib
  │  └──/python/      # python libs
  │   └── /lib/    
  │     └── /python3.6/*    
  ├── /chromedriver/    # lambda layer of headless Chrome 
  │ ├── /chromedriver   # chrome driver
  │ └── /headless-chromium # headless chrome binary
  └── /serverless.yaml     
── /lambda/            # lambda function
  ├── /handler.py      # source code of lambda function 
  └── /serverless.yaml # serverless config
```
### Stack

- Python3.6
- Selenium2.37
- [ChromeDriver2.37](https://sites.google.com/a/chromium.org/chromedriver/downloads)
- [Serverless Chrome v1.0.0.41 ](https://github.com/adieuadieu/serverless-chrome/releases?after=v1.0.0-46)


### Install
Go to root directory of project
```buildoutcfg
# download Selenium 2.37
$ pip3.6 install -t seleniumLayer/selenium/python/lib/python3.6/site-packages selenium==2.37

# download chrome driver
$ cd seleniumLayer
$ mkdir chromedriver
$ cd chromedriver
$ curl -SL https://chromedriver.storage.googleapis.com/2.37/chromedriver_linux64.zip > chromedriver.zip
$ unzip chromedriver.zip
$ rm chromedriver.zip

# download chrome binary
$ curl -SL https://github.com/adieuadieu/serverless-chrome/releases/download/v1.0.0-41/stable-headless-chromium-amazonlinux-2017-03.zip > headless-chromium.zip
$ unzip headless-chromium.zip
$ rm headless-chromium.zip

```

### Install serverless command
Do this if you don't have serverless in your machine yet
```Try running,
npm config set prefix /usr/local
and then,
npm i -g serverless
```

### Deploy Lambda Layers
Go to root directory of project
```buildoutcfg
$ cd seleniumLayer
$ sls deploy 
```

### Deploy Lambda Function
Go to root directory of project
```buildoutcfg
$ cd lambda
$ sls deploy 
```

### Start Testing 
Go to root directory of project
```buildoutcfg
$ cd lambda
$ sls invoke --function hello
```

# loopback-connector-sendgrid
[![view on npm](http://img.shields.io/npm/v/loopback-connector-sendgrid.svg?style=flat)](https://www.npmjs.org/package/loopback-connector-sendgrid)
[![npm module downloads per month](http://img.shields.io/npm/dm/loopback-connector-sendgrid.svg?style=flat)](https://www.npmjs.org/package/loopback-connector-sendgrid)
[![Dependency status](https://david-dm.org/Cellarise/loopback-connector-sendgrid.svg?style=flat)](https://david-dm.org/Cellarise/loopback-connector-sendgrid)
[![Build Status](https://travis-ci.org/Cellarise/loopback-connector-sendgrid.svg?branch=master)](https://travis-ci.org/Cellarise/loopback-connector-sendgrid)
[![Code
Climate](https://codeclimate.com/github/Cellarise/loopback-connector-sendgrid/badges/gpa.svg)](https://codeclimate.com/github/Cellarise/loopback-connector-sendgrid)
[![Test Coverage](https://codeclimate.com/github/Cellarise/loopback-connector-sendgrid/badges/coverage.svg)](https://codeclimate.com/github/Cellarise/loopback-connector-sendgrid/badges/coverage.svg)

> Loopback connector module which allow to send emails via SendGrid


## Installation

````sh
npm install loopback-connector-sendgrid --save
````

## Configuration

### Sendgrid username and password

Use the following configuration if you have a username and password.

datasources.json

    {
        "sendgrid": {
            "connector": "loopback-connector-sendgrid",
            "api_user": '[your username here]'
            "api_key": '[your password here]'
        }
    }

model-config.json

    {
        "Email": {
            "dataSource": "sendgrid",
            "public": false
        }
    }

Configuration in JavaScript

    var DataSource = require('loopback-datasource-juggler').DataSource;
    var dsSendGrid = new DataSource('loopback-connector-sendgrid', {
        api_user: '[your username here]'
        api_key: '[your password here]'
    });
    loopback.Email.attachTo(dsSendGrid);

### Sendgrid API key

Use the following configuration if you have an api key.

datasources.json

    {
        "sendgrid": {
            "connector": "loopback-connector-sendgrid",
            "api_key": '[your api key here]'
        }
    }

model-config.json

    {
        "Email": {
            "dataSource": "sendgrid",
            "public": false
        }
    }

Configuration in JavaScript

    var DataSource = require('loopback-datasource-juggler').DataSource;
    var dsSendGrid = new DataSource('loopback-connector-sendgrid', {
        api_key: '[your api key here]'
    });
    loopback.Email.attachTo(dsSendGrid);

## Usage

Basic option same as built in Loopback

    loopback.Email.send({
        to: "test@to.com",
        from: "test@from.com",
        subject: "subject",
        text: "text message",
        html: "html <b>message</b>"
    },
    function(err, result) {
        if(err) {
            console.log('Upppss something crash');
            return;
        }
        console.log(result);
    });


Send with template:

    loopback.Email.send({
        to: "test@to.com, test2@to.com",
        from: "test@from.com",
        subject: "subject",
        sub: {
            ":name": ["User-1", "User-2"]
        },
        filters: {
            templates: {
                settings: {
                    enable: 1,
                    template_id: "template-id"
                }
            }
        }
    },
    function(err, result) {
        if(err) {
            console.log('Upppss something crash');
            return;
        }
        console.log(result);
    });



# License

MIT License (MIT). All rights not explicitly granted in the license are reserved.

Copyright (c) 2015 John Barry
## Dependencies
[loopback-connector-sendgrid@1.2.3](&quot;https://github.com/Cellarise/loopback-connector-sendgrid&quot;) - &quot;MIT License (MIT)&quot;, 
*documented by [npm-licenses](http://github.com/AceMetrix/npm-license.git)*.


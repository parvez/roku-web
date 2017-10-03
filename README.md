# Roku Remote Web App

Web app for Roku using Roku API

## Getting Started

![Screen 1](https://raw.githubusercontent.com/parvez/roku-web/master/screenshots/screen-1.png)

![Screen 2](https://raw.githubusercontent.com/parvez/roku-web/master/screenshots/screen-2.png)

![Screen 3](https://raw.githubusercontent.com/parvez/roku-web/master/screenshots/screen-3.png)

### Prerequisites

One of the issues working with Roku API was that it does not accept cross origin requests. To overcome the issue, you can make the requests through a proxy that adds the header: "Access-Control-Allow-Origin" "*". I also allowed the webserver accessible only to the internal network 192.168.x.x

```
<VirtualHost *:443>

  <Location /roku>
    ProxyPass http://[YOUR_ROKU_IP_ADDRESS]:8060/
    ProxyPassReverse /
    Header add "Access-Control-Allow-Origin" "*"
    Order deny,allow
    Deny from all
    Allow from 192.168
  </Location>

  <Location />
    Order deny,allow
    Deny from all
    Allow from 192.168
  </Location>

  Alias /custom /var/www

<VirtualHost>
```

### Installing

The files are static html, so you can host them on your webserver along with your roku proxy.


## Built With

* [Roku External Control Service Commands](https://sdkdocs.roku.com/display/sdkdoc/External+Control+API)
* [jQuery](https://jquery.com)
* [bootstrap](https://getbootstrap.com/docs/3.3/)
* [fontAwesome](http://fontawesome.io/)

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/parvez/d84dd4b4b9b32e5fc1d1a99371bc3edc) for details on our code of conduct, and the process for submitting pull requests to us.

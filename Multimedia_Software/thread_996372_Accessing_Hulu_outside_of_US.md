---
title: "Accessing Hulu outside of US"
date: 2008-11-28
forum: Multimedia Software
---

### Post by th89 on 2008-11-28
Hey all, I was poking around Hulu.com, and I stumbled across the way they verify for the US. All they do is pull from this address: [http://releasegeo.hulu.com/geoCheck](http://releasegeo.hulu.com/geoCheck). The format for this is:
```
<?xml version="1.0" encoding="UTF-8"?>
<geocheck>
  <status>valid</status>
</geocheck>
```If the status does not return "valid" it will not play. The next question is, how would you re-direct or modify this to work? Obviously greasemonkey will not work, but like a proxy that would re-direct when this was called might. Just looking for other ideas or possible implementations.

Also, I am already in the US, so this is not a concern for me. Just thought that it may allow other people an easier way to get around it.

---

### Post by albert ozzy on 2009-10-20
i know it's an old thread but i've just tried sth about this:

I edited the /etc/hosts file to redirect releasego.hulu.com to my own webserver. and added geoCheck and crossdomain.xml file to my webserver. when i tried to load them in browser they worked fine. But in the hulu.com website it says there's a problem in my internet connection and i should try again.

i guess hulu uses some additional mechanisms for geolocating.

---


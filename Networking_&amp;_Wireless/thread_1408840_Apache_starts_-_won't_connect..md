---
title: "Apache starts - won't connect."
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Machnikowski on 2010-02-16
I'm helping someone set up a Fivebean VPS with LAMP. I've installed Apache on Ubuntu Karmic 64, and it starts successfully:

```
 foobar@foobar:~# sudo /etc/init.d/apache2 start
 * Starting web server apache2
   ...done.
```

However, I am unable to connect through a web browser. Safari tells me it's because it "cannot connect to the server".

I have tried installing Lynx directly on the VPS and visiting localhost, but that gives me "Alert! Unable to connect to the remote host".

I've set up LAMP on dedicated boxes countless times and have never had any issues, but this is my first time on a VPS. Am I missing something really obvious?

Thanks!

EDIT: CanYouSeeMe.org in Lynx, on the VPS, says "Connection refused"

---

### Post by superprash2003 on 2010-02-17
what happens when you open [http://127.0.0.1](http://127.0.0.1) in the local machine

---


---
title: "rewrite HTTP headers"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by Krzysiek_PL on 2010-04-03
Hi!
Could you recommend light and easy to configure proxy server? Basically  I need one feature: an ability to rewrite headers of HTTP protocol. 
I mean: server receives HTTP request, rewrite 'host' header of this request and sends it to real destination.

---

### Post by jflaker on 2010-04-03
just google "apache rewrite"

One example: [http://www.whoopis.com/howtos/apache-rewrite.html](http://www.whoopis.com/howtos/apache-rewrite.html)   Which explains it a bit......

The idea is you do [http://YourServer/SomeContent....redirects](http://YourServer/SomeContent....redirects) to [http://SomeOtherServer/TheRealContent](http://SomeOtherServer/TheRealContent)....

this is useful if you moved content or moved a sub-domain, etc.

---

### Post by Krzysiek_PL on 2010-04-03
> **jflaker said:**
> just google "apache rewrite"

One example: [http://www.whoopis.com/howtos/apache-rewrite.html](http://www.whoopis.com/howtos/apache-rewrite.html)   Which explains it a bit......

The idea is you do [http://YourServer/SomeContent....redirects](http://YourServer/SomeContent....redirects) to [http://SomeOtherServer/TheRealContent](http://SomeOtherServer/TheRealContent)....

this is useful if you moved content or moved a sub-domain, etc.

Thanks for your reply
...but in my case apache mod_rewrite is useless. Generally I have to connect non-SSL application with SSL web server (apache). This app use HTTP protocol in order to communicate with server. 
At this point I use stunnel to turn on SSL at the client site. This application sends non-SSL request to stunnel and then stunnel sends this request using SSL to server. But doing this in this way server receives request with stunnel's address in host header and reply 503 error witch means that the request isn't for this machine.

---


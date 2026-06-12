---
title: "Port 80 conflict..."
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by kadvar on 2008-12-30
Hi,

I've been trying to setup a web server at home. Apache's installed and everything and I can access my web pages at localhost/192.168.X.X. I've set up port forwarding so that my website is viewable from the internet for which I have a static ip.

The problem is that whenever I type in my public ip (80.46.XX.XXX) into the browser, I get my router configuration page instead of the page served up by apache. The port forwarding IS working, I can see my webpages from other computers when I type in my public ip. It just wont show me my pages from the machine on which I have apache installed. Keeps showing me the router configuration page instead.

The router is a Gigaset SE 587 router from Siemens and the 'remote management' feature is turned Off.

Please tell me if I'm missing something here.

---

### Post by Iowan on 2008-12-31
Are those other computers you mentioned inside the network (behind the router)? I suspect machines inside the network will need to use the local address (192.168.X.X).

---


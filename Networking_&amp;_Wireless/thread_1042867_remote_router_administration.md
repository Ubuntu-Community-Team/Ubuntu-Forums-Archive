---
title: "remote router administration"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by alanwalterthomas on 2009-01-18
I want to connect to my wife's computer halfway across the world which is behind an entry level trendnet wireless router. I know how to use ubuntu's remote desktop viewer well enough over a LAN but this I don't know how to do, or even if it's possible. I want to do that because she finds any kind of configuration (screensaver, resolution etc.) daunting. However, she would have to set up port forwarding on the router, right? Is it possible to connect to the router through the Internet if I have the username/password that I use when I configure it through the local computer? Can anyone tell me what I'd have to do to get then use the router's ip, whether I'd have to set up a static ip for her machine on the LAN, & whatever else is necessary to make this work.
Thanks,

---

### Post by zeronothing on 2009-01-18
this is possible, it would just depend on the routers functionality. I have a netgear and one of the options is remote management. if I were to enable it all I would have to do is open up my web browser and type in the Public IP address with the port number. an example would be:

[http://67.xxx.xxx.xxx:8080](http://67.xxx.xxx.xxx:8080)


after you would type that into the web browser you would get the routers configuration page. like I said it would all depend on the router.

---

### Post by zeronothing on 2009-01-18
do you know the make and model of the router?

---

### Post by superprash2003 on 2009-01-18
usually.. you would have to tell your wife to login to your router locally and enable REMOTE ADMINISTRATION.. most routers have that option.. once enabled.. all you need to do is get that router's public ip by opening [www.whatismyip.com](www.whatismyip.com) on a pc connected to that router locally and then connecting..

---

### Post by alanwalterthomas on 2009-01-18
My Trendnet router is a TEW-432BRP. I looked up the specs & remote administration is among them. I'm not exactly sure in which menu she'll find it but it'll work out. Thanks for the help everyone. If it's not really easy, I'll post back in a month or two asking for more help or explaining the tricks.

---


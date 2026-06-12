---
title: "How to expose a local lan ip to the internet"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by mthalis on 2010-08-30
My local network contain four computers and they have dynamic Internet connection. i want to access one of my local network computer using ip address or name when i am at my office or any other place. so how can i do this sort of thing. I not care about security issues. My network all computer have Ubuntu 10.04 and their ip range is 192.168.1.2 to 192.168.1.6.
Note :- My machine have glass-fish server that what i want to access(using 8080 port) remotely.

---

### Post by squaregoldfish on 2010-08-30
The way to achieve this is to configure port forwarding on your router. So, if you want to run a web server on your machine, you'd set your router to forward port 80 to the IP address of the local machine that's running the web server itself.

Obviously you have to make sure that machine always gets the same IP address, so you don't have to reconfigure your router every time.

Steve.

---

### Post by mthalis on 2010-08-30
I havn't good network knowledge, please exapin how can i do it step by step. Any refence site.
Tanks

---

### Post by squaregoldfish on 2010-08-30
The precise method of setting up port forwarding will depend on your router - check out the router's manual. If you don't have the manual, you should be able to download a copy from the manufacturer's site.

Steve.

---

### Post by Iowan on 2010-08-30
> **mthalis said:**
>  I not care about security issues.> **mthalis said:**
> I havn't good network knowledge...This sounds like a bad mix. Please consider the implications before you open your network to the world...

---

### Post by capn.hector on 2010-08-30
you will also need to set up dynamic dns resolution so that when your isp provided ip changes you will still be able to find your server.

---

### Post by jerome1232 on 2010-08-30
+1

Essentially if you open your glassFish server to the world you need to be aware that everyone can try to abuse and take advantage of the service your exposing.

There are steps you can tak to limit this, such as using ufw to only allow your works ip address to access your service for example, among many other things.


On that note [portforward.com]("http://portforward.com/") has guides for most routers which will show you how to forward a port. Do everything in your power to secure your service, depending on what glassFish is doing and how it's configured, you could be opening your front door to bots, worms, and various attacks.

---


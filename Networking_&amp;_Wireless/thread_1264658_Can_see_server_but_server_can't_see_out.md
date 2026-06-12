---
title: "Can see server but server can't see out"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by byuhobbes on 2009-09-12
I am pretty comfortable with Linux in general and Ubuntu in particular.  I am familiar with installing/managing/updating software and I use Ubuntu as my primary working environment.  However, I have little experience with networking issues.

I have a server that I can access from the web (let's call it server.myuni.edu).  When I go to [http://server.myuni.edu](http://server.myuni.edu), I can see the index page in the web root.  I have no problem accessing any of the web-accessible content on that server.  Additionally, I can log in via SSH.

However, the server can't seem to see out.  Commands like ping and wget say that the server/file can't be found/resolved.  I've tried ifdown eth0 and then ifup eth0, but that didn't work.  I also tried rebooting, but that didn't work.

Does anyone have any suggestions?

---


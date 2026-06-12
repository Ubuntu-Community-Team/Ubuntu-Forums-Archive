---
title: "Strange problem with Gigaset SE361 router: Firefox ok, but terminal very slow"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by liviubero on 2009-05-18
Hi,
first, I have no internet connection problems with this router, I am using it right now, but every time when I try to ping some address (other than 192.168.2.1) from the terminal, I have to wait about one minute or more for some output. ssh doesn't work because I always get "Connection timed out".
What could cause such a problem?
Why can I use Firefox without any problems, but the terminal connection is so slow?

Using a Toshiba Satellite L40-17S with a wired connection through a rtl8139 ethernet card.

Thanks.

---

### Post by liviubero on 2009-05-20
I have just tried in Windows and ping works just fine, so this a Ubuntu problem.
No one had this problem?

---

### Post by kaleidoskop on 2009-11-22
Same problem here. I'm using also the SE361 router of Siemens. In Windows, everything works fine. Any solutions?

---

### Post by lucius.antonius on 2011-05-27
I have the same router (Siemens Gigaset SE361) and similar problems. 

It may be this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757")

A similar problem with this router is discussed here:
[http://ubuntuforums.org/showthread.php?t=1219426]("http://ubuntuforums.org/showthread.php?t=1219426")

---


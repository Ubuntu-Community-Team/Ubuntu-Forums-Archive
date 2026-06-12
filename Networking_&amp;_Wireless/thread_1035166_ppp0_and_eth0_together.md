---
title: "ppp0 and eth0 together"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by subiet on 2009-01-09
I have USB mobile modem (India>Airtel) which get recognized as a ppp0 interface and i can access Internet via it, if i a remove my LAN cable. the LAN is via the eth0 interface and i can access my campus intranet via it. 

Now what i want is that all connections except 10.x.x.x to go through the ppp0 interface and the 10.x.x.x to go via eth0. so that i can use Internet and Intranet together.

Also is it possible that i can share my internet connection (which i have via ppp0) with other people on my campus intranet via the eth0.


i btw also followed the steps on this guide, kindly tell me if i have to undo anything, and if yes how to.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by subiet on 2009-01-15
bump

---

### Post by superprash2003 on 2009-01-15
yes you could setup internet connection sharing .. just follow this .. although you should get your interfaces right..[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by wmdiem on 2009-01-15
"Now what i want is that all connections except 10.x.x.x to go through the ppp0 interface and the 10.x.x.x to go via eth0. so that i can use Internet and Intranet together."
route should do this for you. ```
man route
``` will give you the syntax

---

### Post by subiet on 2009-01-15
thanks, that would be great

---


---
title: "Modem dialing out on boot intermittently"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by wolfgangmcq on 2011-03-22
I have a 56K modem which is dialing out intermittently when I boot. It is using the slamr driver and the 2.6.14-22 kernel. When I start it, it usually (but not always) dials. It seems to be dialing with root permissions, and I don't know enough about boot scripts to be able to figure out why it's dialing & how to disable it.

---

### Post by wolfgangmcq on 2012-03-19
I found the problem. The computer was trying to get the time from a network server on boot.

---


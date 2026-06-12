---
title: "'Acer Nplify' not detected"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by Milkehh on 2010-09-25
Hey I just recently installed ubuntu 10.04 and I am having no luck connecting to my network via wireless. I went into the top right with the little wireless icon to see no networks detected. I tried using lspci which came back with no wireless adapters

[http://paste.ubuntu.com/500375/](http://paste.ubuntu.com/500375/)

if anybody can help me that out that would be great :)


I have an Acer Aspire 4741G (The i5-430M one)


Thanks.

---

### Post by chili555 on 2010-09-25
> 05:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)I believe this is your wireless device. If you can hook up the ethernet and go to System > Administration > Hardware Drivers, I think a driver will be available for download and installation.

---

### Post by ganktard on 2010-09-27
I have a similar problem to the OP. On a Wubi installation I found the driver, however on my Live CD installation no driver can be found... please help!

---

### Post by chili555 on 2010-09-27
Do you have the same card? Please post:```
lspci -nn
rfkill list all
```Thanks.

---


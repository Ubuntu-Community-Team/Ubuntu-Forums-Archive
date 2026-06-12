---
title: "ubuntu can`t see my ethernet"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by mac04 on 2010-12-03
Hi 
Just installed ubuntu onto my desktop  but it dosn`t seem to have drivers installed ,   when i plug ethernet cable in  it cant see it , dosn`t notice it at all  so i cant get onto web to download updates 

thanks

---

### Post by Iowan on 2010-12-03
What hardware do you have? From a terminal (Applications>Accessories>Terminal) check/post results of **sudo lshw -C network**

---

### Post by grahammechanical on 2010-12-03
If you open a terminal and type  nm-tool    you will see a list of devices managed by network manager. I get the following results: Device: wlan0    Device eth0 Device eth1

There is other information that tells me that I am connected by wlan0 and that eth0 is unavailable and that eth1 is disconnected.

What information do you see? There really should be little problem connecting using ethernet.

regards.

---


---
title: "Troubles with D-Link DWA-140"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by wolfgan on 2010-09-25
OS Ubuntu 10.4

I have installed DWA driver as recomended there: [http://http://sudosys.be/?q=D-Link_DWA_140_ubuntu]("http://http//sudosys.be/?q=D-Link_DWA_140_ubuntu")
Before that I was done ```
sudo rmmod rt2800usb rt2x00usb rt2x00lib
sudo gedit /etc/modprobe.d/blacklist.conf
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

```Now I have
```
 lsmod | grep rt
rt2870sta             557965  0 

```and iwconfig returns 
```
 
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

```How can I get it up?

---

### Post by davedub on 2010-09-25
Exactly same here - I'm very new to linux, so please bear with me. It seems to me that my rt2870sta driver is present, the necessary (i.e confilicting) drivers are blacklisted as per other forum posts, but there is still no wireless interface is available / detectable.

This issue seems to have been going on a long time, with most ppl applying the above workaround - but it hasn't worked for me either.

Any help? Please?

 - Davedub

---

### Post by Mattias on 2010-09-25
A me too here, Something is fishy with the current state of drivers.
//Mattias

---

### Post by claypole on 2010-10-04
Try here... [http://ubuntuforums.org/showthread.php?t=1449781](http://ubuntuforums.org/showthread.php?t=1449781) :)

---


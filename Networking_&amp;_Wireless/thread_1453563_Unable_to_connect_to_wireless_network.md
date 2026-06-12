---
title: "Unable to connect to wireless network"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by kundthean on 2010-04-13
Hi, 

I have a Dell Inspiron 1525. I am unable to connect to wireless networks. I have a fresh installation of Ubuntu 8.04. I have installed Ndiswrapper (ndiswrapper-utils_1.8-0ubuntu2_i386.deb) and the GUI for ndiswrapper. 

The ndiwrapper GUI reports that the hardware was not found. Yet I am able to connect to the wlan using Windows. 

Please help get this issue resolved.

Kundan

---

### Post by drpjkurian on 2010-04-13
Hi 
Which type of wireless card do you have.
If it is Atheros wireless please try my thread [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

---

### Post by kundthean on 2010-04-13
Could you tell me how to find out which network driver I have?

---

### Post by drpjkurian on 2010-04-18
> **kundthean said:**
> Could you tell me how to find out which network driver I have?

Hi
Sorry for the delay
Please type the command
```
lshw
```
you will see something like this which describes your wireless, See the screen shot

---


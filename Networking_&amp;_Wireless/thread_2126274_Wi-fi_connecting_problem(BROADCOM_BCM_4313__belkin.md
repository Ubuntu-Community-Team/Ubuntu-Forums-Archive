---
title: "Wi-fi connecting problem(BROADCOM BCM 4313 / belkin surf N300 with ubuntu wubi 12.10)"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by MikeeezZz on 2013-03-16
Hello everybody!

I installed the **wubi** version of ubuntu and I have serius problems with the wi-fi connection, it's like a week that I'm trying to solve it.
Using the broadcom internal wi-fi sometimes I can see the connections and sometimes not but, anyway, I can't connect to them (sometimes it says that I'm connected but if I try to load a page nothing works).
I read in some threads that the peolple solved the problem buying an usb wi-fi connection because a lot of people has problem with the broadcom so I've buyd it. 
Anyway, I didn't solved the problem because the usb doesn't install on ubuntu and I can't find the driver.
Someone has a solution to solve my problem in one of the two ways (broadcom or usb)?

Has written in the title, the model of the internal one is **BROADCOM BCM 4313** while the usb is **belkin surf N300**.
The ubuntu **wubi **version in **12.10**
If it can help, I have an **hp pavillion g6** on **64** bits running **Windows 8** (updated from the 7). 
If possible, it would be better a solutions without connecting to the internet with the cable with ubuntu. For now I can only download and transfer files from windows (with connection) to ubuntu with an usb).

Thank you for the help :)

---

### Post by AlecJ on 2013-03-16
Have a read here

[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)

---

### Post by MikeeezZz on 2013-03-16
> **AlecJ said:**
> Have a read here

[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)

Thank you for the answer.
Here's the result:
input
```
Michele @ ubuntu: ~ $ apt-get install build-essential linux-headers-generic
```
output
```
E: Could not open lock file / var / lib / dpkg / lock - open (13: Permission denied)
E: Unable to acquire the lock on the administration directory (/ var / lib / dpkg /). You must be root.

```

but I don't see the point because I'm root. It maybe can be related with the fact that I have the wubi version of 12.10?

---

### Post by MikeeezZz on 2013-03-16
I also looked in the ubuntu folder from windows to check if there was missing the root file so I've done ubuntu->disks and the file root.disk was there so I don't think something is missing...

---

### Post by MikeeezZz on 2013-03-17
I need help please, I have a work to do and I need the connection with linux as soon as possible :(

---

### Post by mvs1207 on 2013-03-17
Try the command line with **sudo** prefixed..  Your output shows that are not root but Michele.  If you were root you would see **root@ubuntu:~#** as your command prompt

```

Michele @ ubuntu: ~ $ sudo apt-get install build-essential linux-headers-generic

```

---

### Post by wildmanne39 on 2013-03-17
*Thread moved to **Networking & Wireless**.*

---


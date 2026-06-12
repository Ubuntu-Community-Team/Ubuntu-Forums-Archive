---
title: "Linksys AE1000 Wireless Adapter not working"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by CameronC on 2011-02-16
I have a AE1000 wireless adapter and Ive been using it or about 4 months on windows xp.
Yesterday I installed ubuntu 10.10 and it won't work
It won't connect to the internet and won't even show signs that it is turned on.
Im very new to linux and Don't really know what im doing.
If you can help Please
Thanks :D

---

### Post by chili555 on 2011-02-16
Did you read this? [http://ubuntuforums.org/showthread.php?t=1630358&highlight=AE1000](http://ubuntuforums.org/showthread.php?t=1630358&highlight=AE1000)

---

### Post by CameronC on 2011-02-16
YEs I have read that but it lead me nowhere.
I have no internet connection on ubuntu
The only connection I can get is on windows xp which the adapter works.
I need to fix it so it will work on ubuntu
Thanks.

---

### Post by CameronC on 2011-02-16
> **chili555 said:**
> Did you read this? [http://ubuntuforums.org/showthread.php?t=1630358&highlight=AE1000](http://ubuntuforums.org/showthread.php?t=1630358&highlight=AE1000)


Can you explain to me how to get my adapter working?

---

### Post by CameronC on 2011-02-16
Bump??
Help

---

### Post by chili555 on 2011-02-16
As you no doubt have figured out, it's very difficult to install drivers with no way to download drivers. I assume you have a USB key and can download the attached. Drag and drop it to your desktop. Right click it and select 'Extract Here.' A folder will be extracted containing the Windows XP .inf and .sys files.

Drop your Ubuntu install CD or DVD in the tray and open a terminal and do:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```It will complain loudly when it is unable to find the on-line repositories, but will grab the files off the CD. Now do:```
sudo ndiswrapper -i Desktop/xp/2870.inf
sudo depmod -a
sudo modprobe ndiswrapper
```Now is your wireless working?

---

### Post by kahi015 on 2012-03-21
hey can someone help me to download drivers for linksys ae1000-as pls?:confused:

---

### Post by chili555 on 2012-03-21
> **kahi015 said:**
> hey can someone help me to download drivers for linksys ae1000-as pls?:confused:Please show us, from a terminal:```
lsusb
lsb_release -d
```Thanks.

---


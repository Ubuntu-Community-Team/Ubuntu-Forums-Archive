---
title: "Edimax EW-7318USg Problem!"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by N3tMast3r on 2009-10-20
Hello,

I installed the drivers for my brand new Edimax Ex-7318USg following this guide here: electricshaman.com (Linux would not recognized it). After  I installed the drivers, the wireless adapter seems working but it actually isn’t! First of all I need to reboot my pc with the adapter already plugged to my pc every time I want to see the available wireless networks. Then, I can only see them (it does not show me the strength of the signal) and it does not let me connect to any of them, even my own one or the ones with no passwords.
Any help?. This is so wired! I can see the wireless connections but I cannot connect to them!! =( I also tried to install older drivers but nothing... same story =(

The Wireless adapter works fine under windows xp and windows vista.

---

### Post by duanedesign on 2009-10-22
It appears their are two of these devices that have been manufactured leading to some confusion.

```
lsusb
```
will get you either

```
Bus 001 Device 002: ID 148f:2573

Bus 001 Device 002: ID 7392:7318
```

The first one is the one that is working 'out-of-the-box' for people. The second one is the one that some are getting to work by adding  {USB_DEVICE(0x7392,0x7318)},\ under Ralink towards the bottom of the rtmp_def.h

this thread goes through the installation of the rt73 in greater detail (minus the addition to the rtmp_def.h) They detail some configuring and troubleshooting. Might help to see if there is something in there that you have not done.

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

This is also a good post that they have been updating.
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

Good Luck!

---


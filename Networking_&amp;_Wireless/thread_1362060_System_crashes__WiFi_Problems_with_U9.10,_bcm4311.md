---
title: "System crashes / WiFi Problems with U9.10, bcm4311"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by an.erni on 2009-12-22
Hi there

I've always (since Ubuntu 6.06) been a bit struggling using my built-in WiFi card, but using the following lines helped me to connect properly to the access point:

```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo ifconfig eth1 up
sudo iwconfig eth1 essid WgBluemetopf
sudo dhclient eth1
```

See also the old post:
[http://ubuntuforums.org/showthread.php?t=1057154]("http://ubuntuforums.org/showthread.php?t=1057154")


However, since I updated to Ubuntu 9.10, I have several issues with my system:
1. as soon as I'm using WiFi, my system crashes frequently (between 0.1s and 30mins). This means, that I can't move the mouse anymore and either the display shows a "rainbow" or the shell (no X).
2. when I try to update my system using WiFi, the system crashed immediately
3. firefox does not work anymore (--> "Segmentation fault")

Well, where shall I start? Which is the first thing to look into? And how?

Thanks a lot!
Cheers, Andy

Edit: These days, I'm using Opera instead.

---

### Post by an.erni on 2009-12-23
Anybody...?

---

### Post by an.erni on 2009-12-27
Please don't force me to try another distro...
I'm willing to try almost everything, as soon as it sounds reasonable! I just don't know where to start.

---

### Post by an.erni on 2009-12-27
As there is still no answer, I'm wondering if there is a better place to post my issue... If yes, where?

---

### Post by an.erni on 2010-01-10
As there was no reply, I had to do it the ugly way:

After installing Ubuntu 9.10-64 from CD, I just followed this instruction:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=4311]("http://ubuntuforums.org/showthread.php?t=766560&highlight=4311")

After the reboot, the WiFi worked better than ever.

Cheers, Andy

---


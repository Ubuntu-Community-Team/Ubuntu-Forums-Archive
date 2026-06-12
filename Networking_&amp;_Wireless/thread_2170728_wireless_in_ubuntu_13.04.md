---
title: "wireless in ubuntu 13.04"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by m3t3ors on 2013-08-27
just installed 13.04 on my updated dell latitude d520 and got no wireless internet. when i say updated latop i mean ive upgraded memory to 2gig and swapped the wifi card for broadcom bcm4311 802.11b/g
i checked additional drivers and installed the recommended driver, and rebooted. i now have wireless icon (afan in top right corner) but it says no connections available.
help appreciated

---

### Post by Hadaka on 2013-08-27
Hi, from a wired connection please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot

*Note..your wired is probably not working either
it will be after the first ccommand.
Wireless working now??

---

### Post by m3t3ors on 2013-08-27
hmmm. ran your first command and ran ok
ran your second command and i got an error?
looks like ive no ethernet since i installed the recommended driver
jut rebooted gonna try again

---

### Post by m3t3ors on 2013-08-27
thanks for your help, all working

---

### Post by Hadaka on 2013-08-27
Glad that worked for you.
Enjoy !

---


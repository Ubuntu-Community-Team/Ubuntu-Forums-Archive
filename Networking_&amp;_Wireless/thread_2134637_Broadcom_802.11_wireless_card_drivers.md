---
title: "Broadcom 802.11 wireless card drivers"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by starcraft on 2013-04-11
I recently installed Ubuntu 12.10 and first booted into live CD, no wireless support, after install, no wireless support
after visiting multiple threads about the Broadcom drivers, I get a driver package and it is in source code, meaning it is useless to me 
, I want someone here to either find me a compiled drive for the following chipset > Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)    Subsystem: Dell Wireless 1390 WLAN Mini-Card 
I also want to add these things, The computer is a Dell Lattitude d620, and I have already installed the b43 packages and had no luck what so ever
the STA driver from Dell did not work either, and the NDISwrapper guide isn't very helpful for a new linux user
I thank you for any help you give me members.
EDIT: there is no wired internet for us, all WiFi, I am on a different computer

---

### Post by Hadaka on 2013-04-11
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then go here for a zip file and instructions..
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)

---


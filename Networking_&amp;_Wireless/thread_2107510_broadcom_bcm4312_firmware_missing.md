---
title: "broadcom bcm4312 firmware missing"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by aldrich199 on 2013-01-22
can you help me how to fix this problem step by step
im new user of ubuntu 12.04 lts 32 bit

the problem is icant connect to internet using either ethernet or wifi?

dell inspiron 1545
broadcom bcm4312

---

### Post by aldrich199 on 2013-01-22
bump*

---

### Post by ubfan1 on 2013-01-24
On the live installation media, in directory /pool/restricted/b there is a package of Broadcom drivers:
bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb
Try installing this, the (STA aka wl) driver comes with firmware embedded.  The b43 driver you are trying to use is the one needing external firmware.

---

### Post by chili555 on 2013-01-24
Please run:```
lspci -nn
```Is your wireless device enumerated 14e4:4312? If so, I'm afraid the solution above is incorrect. Please get a temporary ethernet connection and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```You should be all set.

---


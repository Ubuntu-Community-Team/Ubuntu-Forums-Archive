---
title: "dell branded broadcom bcm4321 in 12.04"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by abrown0920 on 2013-02-09
I have spent then last six hours reading threads and trying different drivers and I can't make this work.  Of all he threads I read evened the solved I couldn't discern a positive solution. Can someone help me. I am so tired of this I am about ready to give up and by a USB adapter.

---

### Post by ice.simx on 2013-02-13
i'm also facing similar kind of issue, my laptop is dell vostro 1510, wifi is bcm4321.
On earlier version of ubuntu it worked fine, but on 12.04 64-bit facing issue.
will try something tonight and post the result.

---

### Post by TOMBSTONEV2 on 2013-02-13
Try this, in a terminal type: 
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```If this does not solve your problem, you may want to install the b43 drivers and firmware:
```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```Restart the computer then open a terminal and type:
```
sudo modprobe b43
```

---

### Post by abrown0920 on 2013-02-13
Thanks tombstone, I will try tonight and report back. I have tried both drivers at some point butI could have done install wrong and probably didn't restart each time

---


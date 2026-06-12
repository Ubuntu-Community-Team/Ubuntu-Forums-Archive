---
title: "Broadcom BCM4321: 64 bit wireless adapter not working"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by headshrinker101 on 2013-01-27
Have a Broadcom BCM4321 802.11 a/b/g/n card that works fine with kernel 3.4 but when I upgrade to 3.5 the wireless is not recognized.  It worked fine when I ran the 32-bit version with 3.5 but having a 64-bit system I would like to run on 64-bit.  Any ideas?
Thanks in advance.

---

### Post by TOMBSTONEV2 on 2013-01-28
Try this:

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```If that doesn't work go to this website and install b43-fwcuttter firmware, then install the b43 wireless driver.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---


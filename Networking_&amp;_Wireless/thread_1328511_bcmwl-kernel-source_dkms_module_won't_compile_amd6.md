---
title: "bcmwl-kernel-source: dkms module won't compile amd64 Karmic"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by jrduncans on 2009-11-16
I have a BCM4312 wireless card, and I have been trying to install the Broadcom STA proprietary driver.  However, the module fails to compile with messages like:

/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c:220: error: ‘struct net_device’ has no member named ‘open’

The same problem appears to be reported here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492/comments/12](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/441492/comments/12), however that issue in general seems to be for a related but different problem, as reinstalling appears to have fixed the problem, whereas it does not for me.

Should I report a new issue?  Is this related to 64-bit vs 32-bit?

---

### Post by PRC09 on 2009-11-16
Maybe this will help with the install:


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by jrduncans on 2009-11-16
> **PRC09 said:**
> Maybe this will help with the install:


[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

That indicates (as have other research I've done) that BCM4312 support is in progress for the non-proprietary driver, which is why I'm trying to use the STA driver.

---


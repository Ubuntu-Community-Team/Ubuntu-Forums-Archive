---
title: "ppa for latest broadcom wl driver?"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2012-06-08
I noticed that the wl version installed in precise bcmwl package is pretty old. The latest STA driver (5.100.82.112) on Broadcom's site works much better IMO. I can build it from source, the problem is if I upgrade the kernel I need to rebuild. Does anyone know of a ppa that has teh latest driver pre-built for precise?
-J

---

### Post by praseodym on 2012-06-09
Try it via dkms:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

It should be installed "linux-headers-generic" or "linux-headers-generic-pae", respectively, plus "build-essential" and "dkms"

---

### Post by carl4926 on 2012-06-09
Also worthy of note is that b43 is probably going to work for many now, releasing the kernel taint

Check your device here
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---


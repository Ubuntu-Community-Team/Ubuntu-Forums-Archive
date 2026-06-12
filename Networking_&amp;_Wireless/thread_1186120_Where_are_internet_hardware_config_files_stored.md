---
title: "Where are internet hardware config files stored?"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by conjunctivitis on 2009-06-13
Hello,

I'm trying to directly copy all hardware/driver information from my fresh 9.04 installation (with working wireless and lan) to my old 8.10 partition (which, when enabled in fstab, does not detect my networking hardware, nor allow it to function).  

Everything worked fine until the upgrade, and everything works fine post-upgrade until i re-enable the 8.10 home partition in the fstab, at which point wireless and lan leds no longer light, and i have no options under the networking applet menu.  So I'm currently using the default new home partition and every time I want to access my old documents/music/pics, I have to mount the other partition manually and navigate to the stuff, which is a hassle.

I'm hoping I can just cp /home/etc/? /oldhomepartition/home/etc/? for a few config files?  Thanks

Acer Exensa 4420
AMD Athlon X2
Broadcom integrated wireless

---

### Post by conjunctivitis on 2009-06-16
bump

---


---
title: "Restore graphics driver after fglrx"
date: 2009-12-28
forum: Multimedia Software
---

### Post by meech309 on 2009-12-28
I tried to activate the proprietary ATI graphics driver through System > Administration > Hardware Drivers, and when I couldn't get my computer to boot properly -- it just showed a black screen. So I booted in recovery mode and deleted the xorg.conf file from /etc/X11 (probably too hastily, now that I think about it). Now I can log in, but I'm stuck in low graphics mode. Can't use anything but basic visual effects and compiz doesn't work at all. I tried restoring xorg.conf using ```
dpkg-reconfigure -phigh xserver-xorg
``` but it didn't change anything.

Is there a way to restore/recover/reinstall the driver so I can go back to my original graphics setup?

---

### Post by Yellow Pasque on 2009-12-28
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by meech309 on 2009-12-28
Thanks, worked perfectly!

---


---
title: "ATi Radeon 7500 driver conflict"
date: 2009-06-21
forum: Multimedia Software
---

### Post by Necrom@ncer on 2009-06-21
I just messed up my ubuntu install. I use jaunty, and I recently downloaded another driver for my card (I was using the fireGL driver), the exact name I can't remember. I rebooted and  was greeted by a ripped screen. i tried adding this line in terminal:


Driver       "vesa"

In order to get a GUI, but I got the same result. I wanted better resolutions and wanted to see if I got better performance. I was thinking of running apt-get and uninstalling the fglrx driver, is that recommended?

---

### Post by Necrom@ncer on 2009-06-22
C'mon, need help!

---

### Post by Melcar on 2009-06-22
Fglrx does not support that card.  Use the open source radeon driver instead.  Open up /etc/X11/xorg.conf, find the *Device* section, and add the following line:

```
Driver   "radeon"

```


Save and reboot.

---

### Post by Necrom@ncer on 2009-06-22
are you sure? I've been using it and getting resolution up to 1024 and no 3d acceleration, but i'll see about that

---


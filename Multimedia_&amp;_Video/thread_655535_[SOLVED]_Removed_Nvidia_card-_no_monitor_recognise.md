---
title: "[SOLVED] Removed Nvidia card- no monitor recognised"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by sumithar on 2008-01-01
I removed an Nvidia card ('cos I thought it was making my computer lock up) and connected CRT to the card that came with the PC.
Now when I boot up it stops at the message
"running local boot scripts /etc/re/local"

When I hit ctr-alt-f2 and log in at the command prompt and type in the command X, it says "no devices detected"

The contents of my /etc/x11/xorg.conf and the log file are both attached.

Could you help me figure out how to get into gnome, please?

Thanks

---

### Post by taurus on 2008-01-01
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, reboot with

```
shutdown -r now
```

---

### Post by sumithar on 2008-01-01
Great.  That worked, thanks

---


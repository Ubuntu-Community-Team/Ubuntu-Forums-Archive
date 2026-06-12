---
title: "blank screen at startup.."
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by Vanion on 2007-12-24
hi there.  I'm rather new to linux so please bear with me.

recently, after fooling around with my screen resolution settings (which were already set at 1280x1024) the screen now goes blank at startup.  as soon as Ubuntu finished loading, the message "Input not support" floats around my LCD monitor (Acer AL1716).

I have emerald/compiz installed and running.

Any suggestions?

---

### Post by taurus on 2007-12-24
Boot into recovery mode from GRUB menu and reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
```
You can reboot with 

```
shutdown -r now
```

---

### Post by Vanion on 2007-12-25
I did as you instructed and it seemed successful.  however it did not solve my problem :(  still a blank screen.  It might be worth noting at this point that when the screen goes blank, the PC speaker lets out an audible beep.

I'm using an nvidia 6800 GS with the drivers installed

---

### Post by Vanion on 2007-12-25
bump

---


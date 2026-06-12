---
title: "Multiple LIRC remotes"
date: 2012-08-15
forum: Multimedia Software
---

### Post by Fisher on 2012-08-15
Hi, I'm having trouble configuring 2 remotes:
The first one, a ATI Remote Wonder is working fine. I'm using it with XBMC.
I have a ProLink Pixelview MPEG 8000GT, a cx88 based board with ir remote capabilities and decided to use it to control another XBMC instance.
Since I have not found a compatible remote file, I created one with irrecord, and put it in /usr/share/lirc/remotes/black.
In /etc/lirc/lircd.conf when I add this remote and restart lircd, the ATI remote stops working and this remote does not work too.
Although irsend LIST "" "" returns me both remote names, irw cannot receive anything.
I tried playing around with /etc/lirc/hardware.conf with no success.
The ATI Remote begins to work again if I comment the other remote line in /etc/lircd.conf and restart lirc.
I can confirm the remote is working, I tested it with evtest, and it is sending the keystrokes fine.
Any ideas of what is going wrong? Maybe I need to blacklist some modules to disable evdev from grabbing this remote? I have tried in hardware.conf to use de devinput driver too, with no luck either.
I'm using Ubuntu 10.04, in a multiseat configuration and I am afraid to update to 12.04, since I have upgraded my videocard's drivers (Nvidia) once and lost the multiseat capatibilities, also don't know if the new login manager can support multiseat configurations.

---

### Post by Fisher on 2012-08-19
No ideas?...
I'm pretty stuck on this...

---


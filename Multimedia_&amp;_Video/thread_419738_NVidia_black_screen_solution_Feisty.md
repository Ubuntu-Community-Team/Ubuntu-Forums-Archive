---
title: "NVidia black screen solution Feisty"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by necrolin on 2007-04-23
I installed Ubuntu 7.04 and couldn't use the 3D Nvidia drivers. What I saw was:

a) If I installed Nvidia-glx: screen turned off
b) If I installed nvidia-glx-new: blue screen with error message. Couldn't start x-server, something about wrong version numbers,

I found a solution that works at:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Solution using Ubuntu's repositories
a) Remove installed NVidia drivers
b) sudo apt-get install xserver-xorg-dev
c) sudo gedit /etc/default/linux-restricted/modules-common
          add/modify so you see:  DISABLED_MODULES="nv"
d) sudo apt-get install nvidia-glx-new (or install from downloaded drivers, both worked for me)

Now it works for me. Graphics card: geforce 6200

Hope this helps someone.

---

### Post by poekinoeni on 2007-04-23
I installed Feisty on my laptop ( Nvidia Geforce4 440 GO )

The "Restricted Drivers Manager" installs nvidia-glx, rebooted got the "black screen" at login.

I have seen this issue with Fedora 6 so I 

Crtl-Alt-F3, login via command line and edited xorg.conf with nano.

Added this line under - Section "Device"
Option "useDisplayDevice" "DFP"

Rebooted

Everything is seems to work.

Hope this helps.

---

### Post by eponymous on 2007-04-23
how does one boot ubuntu without starting the X server?
i can boot on my motherboard's video card no problem, but then i can't install drivers for the nvidia card (8800 gts) because it isn't "present".

---


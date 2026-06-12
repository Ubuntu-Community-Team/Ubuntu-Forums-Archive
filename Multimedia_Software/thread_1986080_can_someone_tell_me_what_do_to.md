---
title: "can someone tell me what do to?"
date: 2012-05-24
forum: Multimedia Software
---

### Post by cristian.ene on 2012-05-24
Hello,

I have the following fix for the problem that i have, and i don't know how to install it.

nvidia-173 drivers are not compatible with Xorg (ABI to be precise) version released in 12.04.
So I stick with 11.10 version of Xorg. I had to make the following changes to backport Xorg:

 In /etc/apt/sources.list :
 deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

**[COLOR="Red"]i added that to sources list... but the next steps, i don't know how and where and what :)[/COLOR]**
 In /etc/apt/preferences:
 Package: xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050
 Note related to nvidia-173 on Ubuntu 12.04:
I'm using old hardware with nvidia-173 drivers and I don't like the fact  "composite" is mandatory to use Unity correctly (very laggy) I had to  force composite to switch it "off" to avoid laggy windows by modifying  /etc/X11/xorg.conf:
 Section "Extensions"
    Option             "Composite" "Disable"
EndSection

---


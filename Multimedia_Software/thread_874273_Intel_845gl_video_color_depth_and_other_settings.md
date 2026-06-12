---
title: "Intel 845gl video color depth and other settings?"
date: 2008-07-29
forum: Multimedia Software
---

### Post by sdowney717 on 2008-07-29
We put hardy on and it has a minimal xorg.conf
Question is how do you get better resolutions and how do you know what the color depth is, like 16 or 32 bit?
I would prefer 32 bit color. 
We also have trouble with running DVD using any player except totem gstreamer. And I came across a post suggesting to switch color depth from 16 to 32 bit as a fix.
Any one know about the intel driver settings?

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Looks like I found out some info

---

### Post by trash on 2008-07-29
Just install xubuntu hardy on a latitude x300 and xorg is practically empty. I too am stuck in 800x600.
```
sudo dpkg-reconfigure -phigh xserver-xorg
returns... xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080729224044
```

and

```
sudo displayconfig-gtk
```
won't let me change to the intel driver:(

There must be an easier solution than editing xorg all by hand... anybody?

---


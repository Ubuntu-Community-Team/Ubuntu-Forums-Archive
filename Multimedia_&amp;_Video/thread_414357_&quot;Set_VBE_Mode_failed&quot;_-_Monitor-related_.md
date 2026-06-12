---
title: "&quot;Set VBE Mode failed&quot; - Monitor-related Problem"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by Nosedog on 2007-04-19
I'm trying to use Ubuntu 7.04 Desktop AMD64. I have not installed it.

When I try to Start or Install Ubuntu From CD, the X server fails. The error message I got is something like "VESA(0): Set VBE mode failed." 

Starting Ubuntu in safe graphics mode fails with the same error.

Here is my hardware (I'll provide more details if someone needs to know):
- Processor: Core 2 Duo E6300
- Motherboard: Intel D975XBX
- Graphics card: ATI Radeon X1900 XT (this card is not compatible with the open source ati driver.)
- Monitor: ViewSonic VG2230wm (native resolution: 1680x1050, 60 Hz)

I did my own investigation, and I think the problem is with the *monitor*. Before I upgraded to the VG2230wm, I had a very old Sony Multiscan200sx, and Ubuntu booted fine there. But, with the VG2230wm, X.Org seems to detect some strange screen modes, like 1600x1200 and 1920x1440; several modes had resolutions greater than native. I think it's trying to use a bad screen mode for the graphical environment.

I also had this problem with Kubuntu 6.10 Desktop AMD64. Kubuntu takes me to a shell when X server fails, which allows me to edit /etc/X11/xorg.conf. I was able to get X *working* by editing xorg.conf to take out every screen resolution entry except something I know my monitor supports, like 1280x1024, then using the command startx. With regular Ubuntu, I do not get a shell, which makes it impossible to use.

Feature Request: I would like to be able to choose a screen resolution to use for X.Org when booting Ubuntu from the disc.

Since it is probably an issue with X.Org, should I try to contact them?

---


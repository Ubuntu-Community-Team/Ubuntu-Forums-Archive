---
title: "TV doesn't work on boot"
date: 2009-08-09
forum: Multimedia Software
---

### Post by WrinkledCheese on 2009-08-09
Hey everyone,

I normally don't use Ubuntu but I think it's the best choice for my GFs computer.  I'm having a bit of troubles with Ubuntu not properly auto setting the resolution and refresh settings.

I have a fairly old card DX8 compatible.  Not sure it's the issue I think it's something to do with configuration.  Here is me problem in detail.

When I boot the computer with the TV plugged into the VGA port.  It shows the Ubuntu loading screen then once that's done it goes blue and says "NOT SUPPORT".  I'm guessing a resolution or refresh rate isn't set properly.  When I plug in the monitor I can't see anything but part of the background wallpaper and the bottom bar.

If I boot the computer with the monitor plugged in, and then switch to the TV it works.  Is there a way I can set the settings and not have Ubuntu auto-detect every time I boot the machine?

---

### Post by Jenkins1 on 2009-08-09
please post your xorg.conf file it can be found at /etc/X11/xorg.conf . What resolution is your television and what resolution is the monitor?

---

### Post by Jose Catre-Vandis on 2009-08-09
TV probably needs a lower resolution to work properly.

First try editing your /boot/grub/menu.lst, and add 
```
vga=788
```
to your kernel line for ubuntu

Boot up with monitor attached, then change your screen resolution to 800x600.

Shutdown, switch to TV and try it...

---


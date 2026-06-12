---
title: "Resolution issues with widescreen monitor"
date: 2008-07-15
forum: Multimedia Software
---

### Post by smallgodinacan on 2008-07-15
I've been beating my head against the desk all day today over this one. I have a Samsung 19 inch monitor (Model 932bw) and a Nvidia GeForce 6600GT video card. I can not get the X11 to run in the native resolution of 1440 x 900. I have tried pkg-reconfigure xserver-xorg and manually editing the etc/X11/xorg.conf  file,  but the settings will not stick. I have checked the setup in the xconfig setup and the monitor does support it. Any ideas what to try next?

---

### Post by xc3RnbFO8P on 2008-07-15
Try alt+f2
> gksudo displayconfig-gtk
and use Generic 1440x900

---

### Post by smallgodinacan on 2008-07-15
I booted the system up to try that and the configuration had finally stuck. But kudos on the help, I did confirm the settings with that command.

---

### Post by xc3RnbFO8P on 2008-07-15
Mark it as solved :)

---


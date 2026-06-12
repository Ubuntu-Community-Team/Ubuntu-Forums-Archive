---
title: "ATI Question"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-06-07
Does anyone know of a way to get an old ATI Mach64 to work with resolutions higher than 648x480?  I don't need anything special like 3d effects or TV out, I just want to get a display with a usable resolution.  I'm using feisty.

---

### Post by trippinnik on 2007-06-08
How much video memory does it have?  You'll probably want to lower the color to 16bit.  Is your monitor detected correctly?  This stuff can all be changed in /etc/X11/xorg.conf
Also you'll want to find out what driver you are using.  I'm not sure what kind of support there is for the Mach64 though.

---

### Post by josesanders on 2007-06-08
I've tried several drivers, and only the vesa driver works at all.  I can't seem to get the xserver to start wtih the 'ati' driver.  The only reason that I'm using the card is because it's the only pci card that I have, and I'm trying to use it with an agp card to get dual monitors.

---


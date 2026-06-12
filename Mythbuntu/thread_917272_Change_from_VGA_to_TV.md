---
title: "Change from VGA to TV"
date: 2008-09-11
forum: Mythbuntu
---

### Post by Ronno6 on 2008-09-11
Through much fiddling and an update or 2 the 32" 1280X720 TV now displays a smaller picture, and text jiggles and is not clear and  .
when I run 
 sudo ddcprobe    
it returns :

vbe: VESA 3.0 detected
vebdor: NVIDIA Corporation   with info on the board.Then lists resolutions and # of colors up to 1024x768x16m.

Does this mean that the video is configured for VESA output? I am running TV via YPbPr , and want to get back to the original (overscanned) 1280x720, but those settings are not available anywhere. The nvidea drever is "in use" but when I attempt to access the Nvidia X server Settings menu I get the infamous "You do not appear to be using the NVIDIA X driver."

Too bad that Mythbuntu doesn't have a "restore" program.

Any ideas?

---

### Post by Ronno6 on 2008-09-12
Anybody ??
Card is Nvidia 6200FX and somehow Mythbuntu made output VGA. I need to switch back to TV out 720p via component, as I had set up during installation. How would this be done if TV out was disabled during installation?

---


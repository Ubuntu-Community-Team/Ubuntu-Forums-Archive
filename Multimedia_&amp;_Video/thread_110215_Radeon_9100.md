---
title: "Radeon 9100"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by LokiAs2 on 2005-12-30
I can't get hardware acceleration on my Radeon 9100 video card (Breezy 
Badger). I install xorg-driver-fglrx using apt, reboot. The fglrx 
module is present. But when I launch fgl_glxgears it looks somewhat 
strange: there're no gears on the sides of the rotating cube but some 
kind of blinking mirrors, when I exit the program (fgl_glxgears) it 
says:

X Error of failed request:  BadDrawable (invalid Pixmap or Window 
parameter)
  Major opcode of failed request:  14 (X_GetGeometry)
  Resource id in failed request:  0x0
  Serial number of failed request:  59
  Current serial number in output stream:  59

Then the computer freezes completely (only "reset" button helps). Please help me out.

There're also some files I want to attach

---


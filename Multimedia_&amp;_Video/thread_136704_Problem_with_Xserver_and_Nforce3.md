---
title: "Problem with Xserver and Nforce3"
date: 2006-02-26
forum: Multimedia &amp; Video
---

### Post by valentinvas on 2006-02-26
Hi guys. 
I installed Ubuntu, but when I start the Xserver the computer freezes. When I go into recovery mode and start the Xserver it says Failed to initialize HAL. can  you please help me?
This my computer's configuration:
Athlon 64 2800+
Nforce 3 150 chipset
ati radeon 9600

---

### Post by knalle on 2006-02-26
what is your graphicard settings in **/etc/X11/xorg.conf**?

---

### Post by valentinvas on 2006-02-26
Thank you for your answer. I check my xorg.conf
some text:
driver               vesa
Default depth    24

Section        "Monitor"
Identifier      "Generic Monitor"
Option         "DPMS"
HorizSync     30-60
VertRefresh   50-75
Device          "ATI Technologies, Inc. Radeon 9600

---

### Post by knalle on 2006-02-26
vesa should load, how about your modules in the same file?

---

### Post by valentinvas on 2006-02-26
Section "Module"
Load "GLcore"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"

---


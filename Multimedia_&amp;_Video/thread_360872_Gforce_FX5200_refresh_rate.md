---
title: "Gforce FX5200 refresh rate"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by alienexplorers on 2007-02-13
Right now I am able only to access a video refresh rate of 60hz in all resolutions.  I would like to be able to use at least 70hz to eliminate screen flicker.  I am using a 14" CRT with a Horz rate of 30-70 and a Vert Rate of 50-120.  I have tried modelines to no avail. Still stuck at 60hz.

---

### Post by disturbedite on 2007-02-13
does your xorg.conf have the other resolutions/refresh rates listed?  i'd bet not.  since our monitors have the same range, i'd recommend copying over the relevant section from my xorg.conf:

Section "Monitor"
  identifier "Gateway EV700"
  vendorname "Gateway"
  modelname "Gateway EV700"
  HorizSync 30.0-70.0
  VertRefresh 50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  gamma 1.0
EndSection

---

### Post by alienexplorers on 2007-02-13
Thanks for the information.  Tried adding the modelines you listed and lost all video modes except 1024x768@60hz.  Thats worst than where I was before.  At least I had more video modes before, even though they were all at 60hz.

Don

---

### Post by alienexplorers on 2007-02-14
Bump

---

### Post by disturbedite on 2007-02-14
i would just tell you to add/change the refresh rates listed, but i don't know what all those numbers behind them mean.  so it prolly wouldn't work....sorry i couldn't be more helpful.

---

### Post by stillspiraling on 2007-02-14
You could try using the modeline generator to enter all your info and using the line generated from that. (based on what rates you want of course)

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---


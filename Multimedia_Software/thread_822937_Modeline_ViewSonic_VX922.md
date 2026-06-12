---
title: "Modeline ViewSonic VX922"
date: 2008-06-08
forum: Multimedia Software
---

### Post by Hordro on 2008-06-08
Hi all, these are the modelines to 1280x1024 resolution of my monitor (ViewSonic VX922), I hope that you will be useful.

```
Section "Monitor"
Identifier "ViewSonic VX922"
VendorName "ViewSonic"
ModelName "VS10162"
Option "DPMS"
HorizSync 30-82
VertRefresh 50-75

Modeline "1280x1024@60" 108 1280 1528 1640 1688 1024 1062 1065 1066 +hsync +vsync #60Hz, Fh=64.00, Fv=60.09 , clock=108.03Mhz
Modeline "1280x1024@75" 135.00 1280 1528 1672 1688 1024 1062 1065 1066 +hsync +vsync #75Hz, Fh= 80.05, Fv=75.16, clock=135.12

EndSection

```

I used the calculator timings that can be found here [http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html) and I entered the values shown in windowsXP driver.

---

### Post by Yellow Pasque on 2008-06-08
Easier way:
```
cvt -v 1280 1024 60.0Hz
cvt -v 1280 1024 75.0Hz
```

---


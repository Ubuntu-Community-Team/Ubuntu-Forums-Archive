---
title: "(R9250) modeline not working properly with fglrx"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by chaumurky on 2005-10-18
I use a special modeline to output 16:9 PAL timings through the VGA output (it connects to a RGBVH/YPrPb converter). This works fine with the original  "radeon" driver but when I changed to "fglrx" the output flickers vertically - but is horizontally stable (like a bad vertical hold). Is anyone aware of any differences to the way the modeline may be interpreted with the fglrx driver? Here's the modeline. 

Modeline "16:9" 21.750 1024 1116 1220 1392 576 577 580 625 interlace +hsync +vsync


Thanks in advance.

---

### Post by chaumurky on 2006-02-13
It appears that the fglrx driver is not supporting the "interlace" option. That basically excludes linux for my HTPC solution. I hope this situation is rectified soon. :-(

---


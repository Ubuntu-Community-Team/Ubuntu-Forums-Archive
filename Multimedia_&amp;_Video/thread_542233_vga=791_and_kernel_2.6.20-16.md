---
title: "vga=791 and kernel 2.6.20-16"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by ermannobonifazi on 2007-09-03
After the last automatic kernel upgrade (now is 2.6.20-16-generic) the boot parameter vga=791 is no more working and the splash logo during boot is not centered on the screen.
Also switching between varius tty (CTL+ALT+F2) and going back to Xwindow (CTRL+ALT+F7) froze the computer.
Any help?

---

### Post by nonewmsgs on 2007-09-03
maybe try 790

---

### Post by ermannobonifazi on 2007-09-03
Why? There is no 790 in the correct table value, and it works before upgrade to this kernel.

         640x480   800x600   1024x768   1280x1024   1600x1200   Ask user at boot
8 bits   vga=769   vga=771   vga=773    vga=775     vga=796     vga=ask
16 bits  vga=785   vga=788   vga=791    vga=794     vga=798     vga=ask
32 bits  vga=786   vga=789   vga=792    vga=795     vga=799     vga=ask

---


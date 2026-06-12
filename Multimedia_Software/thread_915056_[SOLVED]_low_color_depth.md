---
title: "[SOLVED] low color depth"
date: 2008-09-09
forum: Multimedia Software
---

### Post by nikio on 2008-09-09
After I've installed Ubuntu my ATI x1550 is driven by Vesa at, aparently, a 16-bit color depth
My monitor (LG M228WA 1680x1050) should run in 24-bit mode

I've tried to add the line 
```
DefaultDepth 24
``` 
in the screen section of the xorg.conf file but nothing changed

Any ideas?

---

### Post by wolfen69 on 2008-09-09
did you restart x after making the changes? (ctrl-alt-bksp)

---

### Post by nikio on 2008-09-09
I've rebooted, just to be sure!

---

### Post by nikio on 2008-09-10
God knows why now the problem is solved:
I've installed the radeonhd drivers, resulting in a blacke screen
rebooted in safe mode and started the "try to fix X server" I had my screen back but at 800x600
uninstalled radeonhd
rebboted
and now misteriously I have my 24bit color depth, the xorg.conf file contains nothing new...

---


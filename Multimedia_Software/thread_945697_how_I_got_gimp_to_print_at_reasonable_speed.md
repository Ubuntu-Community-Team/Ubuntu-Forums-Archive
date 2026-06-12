---
title: "how I got gimp to print at reasonable speed"
date: 2008-10-12
forum: Multimedia Software
---

### Post by allmyfingersandtoes on 2008-10-12
I have a laserjet 1200. For a couple years I couldn't get gimp to print images faster than a page every 45 min or so. Gimp was the only app that did this. I've just found that both the gutenprint and foomatic/pxlmono drivers have this problem, but the foomatic/hpijs driver does not (5 - 10 sec/page). Matter of fact, foomatic/hpijs is currently the recommended driver for my printer (a change since I installed the printer), but I had to go into the ubuntu printers dialog and ask to replace my driver in order to find that out.

For the sake of completeness I'll mention another suggestion I've seen: if your printer is black and white, you can explicitly ask gimp to print in grayscale (under Printing > Advanced > Printout Mode). But this doesn't affect speed for me with foomatic/hpijs and I didn't try it with the other drivers.

Hope this helps someone.

---


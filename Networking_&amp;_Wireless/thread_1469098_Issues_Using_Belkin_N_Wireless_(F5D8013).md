---
title: "Issues Using Belkin N Wireless (F5D8013)"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by DLBack on 2010-05-01
I have a Belkin N wireless card (model F5D8013 version 1) that is not currently working with my machine.  I have tried several methods appearing on this forum for installation and cannot seem to get this to work properly. Can someone guide me through this?

This wireless card previously worked on this computer when Windows XP was in use.  I am currently using Ubuntu version 9.04 (Jaunty) on a Dell Inspiron 2200. Below appears my results when entering "lspci" into Terminal:

[Removed results of "lspci" terminal command from original post]

**UPDATE: **It turns out that ndiswrapper was not fully installing the driver for this card due to the file's location. A few walkthroughs previously posted about this specific card instructed me to save the .inf and .sys files to the desktop. When the files were accessed from the desktop nothing would install correctly. When I created a new folder for these two files to reside in off the desktop ndiswrapper suddenly made everything load properly.

---


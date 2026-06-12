---
title: "blank screen on resume from hibernate"
date: 2010-01-03
forum: Multimedia Software
---

### Post by jtspencer on 2010-01-03
on a fresh install of 9.10, when I suspended to Ram, on wakeup, the screen would go blank or show a text login prompt but not accept keystrokes, and it appeared to be hung.  This did not happen with the liveCD.

I was able to determine it was NOT hung.  I switched to a text console using ctrl+alt+F6 (any of them would work), then back to X with ctrl+alt+F7.  This restored my gui, though my PS/2 mouse was dead.  A USB mouse would still work.

I checked for lot's of differences between the installed system and the liveCD, and didn't find many.  The big thing that stuck out at me was the use of PAE in my install.  I used the package management system to install linux-386 (a non-PAE kernel), and now it works great, ps/2 mouse and all.

I suspect some bad interaction with PAE and intel graphics driver.

---


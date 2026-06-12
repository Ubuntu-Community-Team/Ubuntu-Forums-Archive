---
title: "horizontal line offset display issue"
date: 2012-09-19
forum: Multimedia Software
---

### Post by Simonpatp on 2012-09-19
After a while of using my computer, some graphics get skewed horizontally. Suspending usually causes it, but just general use can also. Graphics is Intel (Intel® GM45 Express Chipset), 32 bit Ubuntu 12.04 on encrypted (dm-crypt) LVM. Acer Aspire 6930.
It often affects moving areas (like buttons and tooltips on unity launcher) and the desktop. Hovering over the buttons (causing a re-draw) clears them up usually. Each indivitual line is skewed, so in some cases icons are completely unreadable, though they are all skewed by the same amount, causing obvious blockiness.

Picture attached.

---

### Post by Simonpatp on 2012-09-27
This is really annoying. It seems to have started a month or so ago, but got really annoying the past few weeks. Even Gnome3/Cinnamon do it, but not as bad a Compiz/Unity. Any Ideas?

---

### Post by Simonpatp on 2013-01-15
This issue seems to wax and wane, but is more prominent when switching monitors (plugging one in or removing it). Last night my entire screen was completely offset with these lines (including reloading firefox pages) which makes me suspect its a compiz issue, However I was running cinnamon (clutter based) so it must be in the graphics driver? Either way 8.04-10.10 never had any issues with this hardware. Any ideas?

---

### Post by tgalati4 on 2013-01-15
It looks like a video RAM issue.  Perhaps your video RAM is failing?  Does this machine use video memory sharing with main RAM?  If so, minimize it in BIOS or try different RAM sizes and see if the problem is more or less severe.

Sometimes graphical gliches show up in /var/log/Xorg.0.log.

---

### Post by Simonpatp on 2013-01-15
Hmm, I don't see anything in the logs that look like it. I'll check the BIOS later, though 10.10 still runs perfectly for days. 12.04 usually starts "lining" after a day or so (varies greatly)

---

### Post by tgalati4 on 2013-01-16
Try a different window manager like Linux Mint Mate and see if you have the same issue.  If it runs OK on 10.10 then perhaps it's a video RAM leak in the Intel graphics module.  Perhaps post a but report?

---

### Post by Simonpatp on 2013-01-16
It shows up in both Compiz/unity and Clutter/Mutter/Muffin.
Where would I post the bug report?

---

### Post by tgalati4 on 2013-01-16
[https://wiki.ubuntu.com/Unity/FilingBugs](https://wiki.ubuntu.com/Unity/FilingBugs)

---


---
title: "Which wifi USB adapter should I buy"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by Richbuntu on 2011-08-30
I want to buy a wifi USB adapter for my Ubuntu 10.04 computer, can someone recommend me on one that works out of the box?

---

### Post by walt.smith1960 on 2011-08-30
The only adapter I have that works out of the box with 10.04 is a Trendnet TEW-424UB v3.1.  It's an oldie but a goody for me.  Downside is it's G speed, not N. Version matters with this adapter.  There was a version 2.x years ago which used an SiS chipset and the only way to use it was with NDISwrapper.    I have two adapters that run N150 but both require a tweak for Ubuntus <11.04.  I've been happy with a Netgear WNA1100 but I used this installer from sourceforge for it:
[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/)


I have a couple TrendNet  TEW648UBs that work well with laptops due to their small size (and CompUSA had 'em for $14.99).  They use RealTek 8192SU chips for which the firmware is missing in 10.04.  The fix is pretty simple.  Here's a link to the fix and firmware source:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)
Download the firmware file, place it in its proper place and restart.  The blue light comes on and life is good until I suspend and resume.  I had to unplug and replug in order to get it to work.  Chili555 had the solution:
[http://ubuntuforums.org/showthread.php?t=1745769&highlight=suspend](http://ubuntuforums.org/showthread.php?t=1745769&highlight=suspend).
There may be other plug & play N speed adapters but I have no experience.  I hope this is helpful in your decision making.

---


---
title: "Problems with Ubuntu 11.04 Firefox/Chromium and Java"
date: 2011-05-09
forum: Multimedia Software
---

### Post by cecilx22 on 2011-05-09
I'm having problems getting Java working correctly in both Firefox and Chromium. Fun part: the misbehavior is different in both!

In Firefox, certain java apps experience serious rendering errors (see attached). This is most obvious at [www.pogo.com](www.pogo.com) (see screenshot attached)

In Chromium, a lot of java apps just don't load at all. Again, this happens most often on [www.pogo.com](www.pogo.com) with certain games. Not sure what, if anything, to attach for this problem.

This happens on both my laptop and my wifes. She has an nVidia card, my system has an ATI card. These problems happened with both upgrades from 10.10 and fresh installs of 11.04 (all x64). Happens with IcedTea as well as Java (x64).

Not sure what else to try at this point. Please help!  Thanks!

---

### Post by sommersb on 2011-06-22
[SIZE=3]I just built a new 11.04 box and had Java issues on an admin screen I use at work.  The solution was to uninstall the IcedTea plugin.  

Before I did this, when I looked at my plugins list in Firefox, I saw IcedTea but not Java6.  After I uninstalled IcedTea, the java plugin shows up as an installed plugin and the website works properly


[/SIZE]

---


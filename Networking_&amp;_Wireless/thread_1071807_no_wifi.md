---
title: "no wifi"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by ltchronic302 on 2009-02-16
hey guys, sorry if this has been covered numerous times but it seems that none of the threads ive seen here or anywhere else on the internet for that matter have helped my situation(mostly due to outdated links or previous versions of the software or ubuntu distros). Ive got an hp pavillion dv6700 laptop that came with vista installed on it, then i put vista 64 bit and then down to xp professional. Just today I downloaded and installed the latest 64bit version of unbuntu and everything seems to work great except my video driver and my wireless(thank god i have ethernet). Right out of the box i got the hardware driver box saying its using Support for Atheros 802.11 wireless LAN cards and I have 2 nvidia accelerated graphics drivers, one is version 173 and 177 with (recommended) next to it so i disabled the 173 and told it to use 177. I can now change the resolution and use the desktop effects but when i try to play chess in 3d it tells me python opengl support and no python gtkglext support. My main problem is the atheros wifi heres a screen shot of what the terminal says. If atheros chipsets are such a pain in the **** and i cant get this fixed what wireless g pci card should i go pick up that is more friendly to linux?

---

### Post by ieee488 on 2009-02-17
[http://ubuntuforums.org/showthread.php?t=1040557&highlight=wifi+box](http://ubuntuforums.org/showthread.php?t=1040557&highlight=wifi+box)

---

### Post by superprash2003 on 2009-02-17
your output shows you have an atheros card.. hope this helps [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by Ketara on 2009-02-17
There are several ways to get an Atheros 242x card working, so I don't think you'll have to buy a new card. There's generally one or two threads a day about people who have this card, it's kind of funny.

Try: [http://ubuntuforums.org/showthread.php?t=1026770](http://ubuntuforums.org/showthread.php?t=1026770)

If that doesn't work (it didn't work for me w. an HP dv8000 series laptop) you can also try ndiswrapper, although that will be a bit more difficult.

I'm not sure that the backports solution on that thread works for 64bit Intrepid however. Does anybody know?

If it doesn't work, I'd suggest switching to 32bit before shelling out money for a different card, since I know you'll be able to get your card working there. I think you should be okay with 64bit however.

---

### Post by ltchronic302 on 2009-02-19
thanks guys got it working!!:p

---


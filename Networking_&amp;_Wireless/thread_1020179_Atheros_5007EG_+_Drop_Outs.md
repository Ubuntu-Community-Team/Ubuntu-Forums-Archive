---
title: "Atheros 5007EG + Drop Outs"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by Butholigon on 2008-12-23
Hello, i have an Atheros 5007EG (at least i think i do, in XP it detected and worked fine as that) the problem i have is that my wifi card detects, connects but fluctuates in speed when use the internet. Also intermittent drop outs.

Got wifi card to work by installing the linux back port module intrepid. Disabling the other driver in System > Administration > Hardware Drivers. 

Also added 3 blacklist lines to etc/modprobe.d/blacklist (didnt do anything)

Also tried switching to Wicd network manager.

Im somewhat new to linux / have tried searching all over for a fix, im not sure if the mad wifi one is the way to go or if it was outdated by implementation of ubuntu 8.10. 

Any help or links to other threads would be great.

----------------------------------------------------------

Fixed it by following [http://atylmo.wordpress.com/2008/07/04/atheros-5007eg-on-ubuntu-using-ndiswrappe/](http://atylmo.wordpress.com/2008/07/04/atheros-5007eg-on-ubuntu-using-ndiswrappe/)



Cheers

---


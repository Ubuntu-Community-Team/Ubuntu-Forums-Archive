---
title: "Lost my wireless, all my wireless"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by ToddFisher on 2009-07-19
Hello, I have been running Xubuntu 9.04 for a few weeks.  This morning it was working, then started having issues staying connected and re-connecting.  Eventually decided to reboot and see if it cleared up.  Now my wireless manager is gone, no option to enable wireless, nada.  Anyone else have this issue?  How do I fix it?

I've got an Acer Aspire One AOA-110 running Xubuntu 9.04.

Thanks!

---

### Post by Brummy137 on 2009-07-19
I'm having the exact same issue with 9.04 netbook remix Asus 1000HE eee netbook.  The network connectivity applet shows me as having only the lo interface available, when previously it was picking up a variety of wireless networks in the vicinity.

---

### Post by ToddFisher on 2009-07-19
Strangely enough, turning it off for a few hours and wireless manager pops back up.  Really strange since I had rebooted several times and that did not work.

PS  Be careful with NBR 9.04 - I had it but it got corrupted going from NBR to advanced mode.

---

### Post by RedSingularity on 2009-07-19
> **Brummy137 said:**
> I'm having the exact same issue with 9.04 netbook remix Asus 1000HE eee netbook.  The network connectivity applet shows me as having only the lo interface available, when previously it was picking up a variety of wireless networks in the vicinity.


Is your driver installed?  Look in System>Admin>Hardware drivers.

---

### Post by Brummy137 on 2009-07-20
I have found a way to work around my wireless problem for the time being.  If I boot using the most recent kernel 2.6.28-13 then my wireless (and eth0) are broken.  If I boot with the previous kernel 2.6.28-11 then everything works as intended. 

Is this a short term issue that might be fixed when they provide the next kernel update, or is there something I need to do proactively on my part to get things working again? 

Going to Sys>Admin>Hardware Drivers told me that there were no proprietary drivers in use on my netbook.

---

### Post by RedSingularity on 2009-07-20
Sounds like the kernel update did it.  What is the output of lspci ?

---


---
title: "Can not connect to LAN"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Nelbomber on 2009-06-18
I've done some searching (before and after i found the solution), and I am new to Linux, so don't shoot me if this is already somewhere.

**Issue:** After startup my Ethernet connection can not connect (Says no connection established).  This was intermittent (It would connect once out of 40 times, NOTE: it only connected once before I found the solutoin) and was pretty frustrating.

**Background: ** I am running a dual boot (Ubuntu 9.04/WinXP) on an Acer Aspire 5100.  The Ethernet connect established fine in XP, but not in Linux. I originally thought i was a driver issue, but installing new drivers didn't solve the problem.

**Solution:** I noticed that when I was booting into WinXP the computer would connect to the router after the OS had loaded, and that my gf's laptop connected as soon as the computer posted.

  _Wake on LAN_ was disabled in the BIOS.  After I re-enabled it the problem was solved.  It seems Linux isn't enabling the net cards on boot (this may be solved somewhere, I just don't know enough to recognize that yet.)  If it's not out there, Cheers!

---


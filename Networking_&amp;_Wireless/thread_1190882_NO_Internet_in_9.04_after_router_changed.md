---
title: "NO Internet in 9.04 after router changed"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by Gabtevez on 2009-06-18
Hi 
 
I can't access to the Internet after changing the Router from SMC to SpeedTouch. I choose the Auto Ethernet in Network Connections and I put the Mac Address. 
 
anybody can help me ??

---

### Post by Nelbomber on 2009-06-18
I'd done some searching (before and after i found the solution), and I am new to Linux, so don't shoot me if this is already somewhere.

**Issue:** After startup my Ethernet connection can not connect.  This was intermittent (It would connect once out of 40 times) and was pretty frustrating.

**Background: ** I am running a dual boot (Ubuntu 9.04/WinXP) on an Acer Aspire 5100.  The Ethernet connect established fine in XP, but not in Linux. I originally thought it was a driver issue, but installing new drivers didn't solve the problem.

**Solution:** I noticed that when I was booting into WinXP the computer would connect to the router after the OS had loaded, and that my gf's laptop connected as soon as the computer posted.

  _Wake on LAN_ was disabled in the BIOS.  After I re-enabled it the problem was solved.  It seems Linux isn't enabling the net cards on boot (this may be solved somewhere, I just don't know enough to recognize that yet.)

I don't know if you're maybe having the same issue I was or not, but never the less here it is.

---


---
title: "ZD1211RW not reporting Power Levels in 9.10"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by tanlouis on 2009-11-13
Hey all,

I'm using a wireless card using the ZyDAS 1211 chipset and the zd1211rw driver. Everything is working perfectly (including packet injection etc), except for the fact that airodump-ng  reports the power levels as "0"

It was working perfectly fine in 9.04, so the upgrade definitely broke it. I spent hours looking online, but I couldn't find a solution.

FYI, when I go to iwconfig, it tells me the signal level and link quality there....except I have to constantly hit it 100000 times in order to find the best location to put my wifi card.

Thanks
p.s - If anyone knows of any tool that constantly reports the signal strength, I could use that as an alternative too.
p.s.s - Kismet reports "Server is not reporting card power levels"

---

### Post by werzy33 on 2010-01-03
> **tanlouis said:**
> Hey all,

I'm using a wireless card using the ZyDAS 1211 chipset and the zd1211rw driver. Everything is working perfectly (including packet injection etc), except for the fact that airodump-ng  reports the power levels as "0"

It was working perfectly fine in 9.04, so the upgrade definitely broke it. I spent hours looking online, but I couldn't find a solution.

FYI, when I go to iwconfig, it tells me the signal level and link quality there....except I have to constantly hit it 100000 times in order to find the best location to put my wifi card.

Thanks
p.s - If anyone knows of any tool that constantly reports the signal strength, I could use that as an alternative too.
p.s.s - Kismet reports "Server is not reporting card power levels"
I seem to have the same problem.  I have not used Aircrack-ng since before Ubuntu 9.10 which I use now, but the PWR column withing airodump-ng is 0 for all clients.  I have recompiled different versions of the zd1211rw driver, with and w/o the injection patch, tried different versions of aircrack-ng with no luck.  The driver otherwise works fine, that is for normal networking, including signal strength of available clients.

---


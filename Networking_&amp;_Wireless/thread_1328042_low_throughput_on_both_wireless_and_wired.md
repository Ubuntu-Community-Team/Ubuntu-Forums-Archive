---
title: "low throughput on both wireless and wired"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by doccali on 2009-11-16
I'm working on setting up a new computer for MythTV, blueray's etc.  Most of the stuff is running well, but I'm having issues with my network throughput.  My throughput caps at about 60KBps for both wired and wireless.  I've tried a few different things and am pretty sure it's something to do with Ubuntu.  To isolate it as being the computer, I've tried a few different things.  I think the most telling was installing something through Synaptec using the Ubuntu repo's, my netbook gets 300+ KBps, this one gets 60KBps, both over the same wireless connection.

I've also checked to see if it was the wireless adapter.  I hooked a crossover cable up between my netbook and this computer, file transfers still ran at 60KBps.

When I looked at my ethernet connection with ethtools, it reported the connection as being 100Mbps full duplex.  I'd expect my thoughput to be 6 to 8 MBps.

Similarly, when I check my wireless connection with iwconfig, it reports my bit rate at 54mbps, which I would expect to translate in 2 to 3 MBps throughput.

I'm a little stumped on what to try next.  I feel that I've exhausted the hardware possibilities, but I'm not sure why, or how it would be the OS or WICD.

Any help on what to try would be greatly appreciated.

---


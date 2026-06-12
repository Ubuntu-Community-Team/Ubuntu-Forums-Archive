---
title: "Reconfiguring wireless after 6.06 upgrade"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by p2sun on 2006-07-12
After many hours, I finally got my Dell 1450 USB wireless working with Ubuntu 5.10.  Among the first things I did was upgrade to Dapper (6.06), and now I can't get network access.

One of the problems is that ndiswrapper names it wlan0 (as did 5.10), but 6.06 names it eth1 ... (why would they do that?).  So I set up eth1 as an alias for wlan0, and got ndiswapper to install the DELLNIC driver.  When I type "ndiswrapper -l", I see that the driver is installed and the hardware is present.

Now, using the same methods that I used for installing it in 5.10 (iwconfig to set the essid, etc.) the card fails to find the network when I use "iwlist eth1 scan".

I've tried quite a few other things as well.  Anybody have any ideas?

Thanks.

---


---
title: "Auto Eth0 = Never after hard reset"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by SKnudson on 2011-03-04
Hi,

After booting 64 bit 10.10 this morning, the start up hung before entering the GUI and forced me to hard reset. I selected the first option from the boot screen (uname -a shows 2.6.35.27-generic #48 Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux), but my auto eth0 shows "never" and I can't seem to figure out how to reconnect to the Internet on my wired internet connection. Everything was working fine as of yesterday, but the recent slew of updates in the update manager seem to be giving me problems related to Internet usage; frequent flash crashes are a problem on my end now.

I'm using a Windows XP client on the network and everything is working as it should. I've tried the standard unplug modem and router with no luck. I've also removed the auto lo and iface lo remarks from etc/network/interfaces, which have since been put back in. Pinging google from the terminal returns nothing as well.

I'm probably going to end up breaking more than I should, so time to turn to the forum. Not how I wanted to start my day, but let's see if we can salvage what remains.

Thanks

---


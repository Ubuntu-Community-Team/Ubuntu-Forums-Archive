---
title: "MSI CR620 Wireless Issue [10.10]"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by Fungle10 on 2011-01-04
Hey this is my first time here!

I have a problem, When I boot up Ubuntu 10.10 I cannot find or connect to any wireless networks.

I followed the ubuntu help site telling me to use this command:

> sudo lshw -C network

What I get returned is that the Wireless network is disabled but the physical is enabled like so:

> *network DISABLED

I am using 64-Bit Ubuntu by the way.

I looked around the forums but it doesn't seem to work the solutions given, also their adaptors seem to be atheros and mine returns as Realtec.

---

### Post by PatchesTheCaveman on 2011-01-04
Another user of Realtek hardware had luck with installing the official drivers from Realtek and disabling 802.11n:  [http://ubuntuforums.org/showthread.php?t=1659802](http://ubuntuforums.org/showthread.php?t=1659802)

---


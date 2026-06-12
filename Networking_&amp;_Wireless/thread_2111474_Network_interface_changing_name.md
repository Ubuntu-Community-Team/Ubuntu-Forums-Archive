---
title: "Network interface changing name"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by id10tuser on 2013-02-02
I have a Dell XPS 8500 running Ubuntu 12.10.  This machine has a single wired network interface built into the motherboard.  Most of the time this interface is p3p1, but sometimes it is identified as p3p2.  While I was just goofing around with the machine I just put an entry into /etc/network/interfaces for each of them and told them to use DHCP.  This worked though the delay in booting while the one interface timed out was somewhat annoying.  The machine also has a wireless interface but that one is always identified as wlan0.

Now I am trying to learn a little bit about some other software but it wants a static IP.  I am sure that I am just doing something stupid, but I can not figure out how to fix this.  I read a little bit about Consistent Network Device Naming/biosdevname and based on what I read I would think the interface should be called em0 or something similar.  Has anyone experienced this problem and know of a way to fix it?

---


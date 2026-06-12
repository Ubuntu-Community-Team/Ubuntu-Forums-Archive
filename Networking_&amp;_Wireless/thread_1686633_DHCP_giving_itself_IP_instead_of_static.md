---
title: "DHCP giving itself IP instead of static"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by wesg on 2011-02-12
I had my Ubuntu DHCP server running nicely today, but recently I'm seeing some weird behaviour that I don't understand. 

eth1 is facing the internet, and it gets its IP from my modem. 

eth0 is facing the LAN, and runs the DHCP server. When everything is working properly, this has an IP of 192.168.0.2. Now though after I restart the networking, i get the proper IP for about 4 or 5 minutes, before the IP is released for one in the DHCP server pool. It's giving itself an IP on eth0 which means the routing is all messed up. 

I don't understand why it would give itself an IP when the networking interface file says static. 

Suggestions?

---

### Post by wesg on 2011-02-12
Following another forum post I killed a process of dhclient linked to eth0 but that didn't do it. Every 10 minutes it gets a new IP from the DHCP server. It's almost like the DHCP server hasn't latched onto the eth0 interface or something.

** EDIT **
The saga continues: I removed vnstat, reset networking, and everything seems to be working. For some reason, vnstat is activating dhclient and overwriting my network configuration, or something similar. 

I want vnstat to work, though, so what's next?

---


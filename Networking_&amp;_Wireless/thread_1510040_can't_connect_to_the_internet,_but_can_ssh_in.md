---
title: "can't connect to the internet, but can ssh in"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by aimlessiam on 2010-06-15
Hi,
I'm pretty new to Ubuntu, and have run into problem after problem with networking.  The current one: I can't ssh out or connect to the internet, and ping gives a "unknown host" or "network is unreachable". BUT I can ssh into my computer from others on my network. "route -n" gives 2 entries, neither of which is "default", which from my reading it seems like you need, but I don't know how to remedy that. 

Is this a DHCP problem? I'm on a university network, so I doubt it's a problem at their end, but I don't think I changed anything when this suddenly stopped working... 

On a more meta level, is it normal to run into a different network connection problem every few weeks? I'm not touching anything,  I swear! Every linux user I know seems to know ping/ifconfig/route/netstat like the back of their hand, and if it's always like this, it's enough to drive a girl back to windows :(

thanks!

---

### Post by Iowan on 2010-06-15
Probably just **route** will show you "default" - **route -n** gives numeric results. Information should still be there, though. Could you post results of **route -n**? You might also check (post) nameservers (via **cat /etc/resolv.conf**).

---


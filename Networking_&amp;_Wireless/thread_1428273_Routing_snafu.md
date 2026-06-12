---
title: "Routing snafu"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by getut on 2010-03-12
I am fighting a weird routing issue with my Karmic 64bit desktop PC. It is located at a corporate site where the default gateway address leads to the internet as well as to some VPN's.

My Ubuntu machine refuses to work over the VPN. It is getting address and routes assigned by DHCP server. A long time ago I found out classless static routes assigned by a MS DHCP server required a change to the /etc/dhcp3/dhclient.conf. The first option line in that file needs the code changed to 249 and then classless static routes start working in linux.

Except for this one.

I can put a windows machine on this same IP address and it communicates fine, so it isn't a routing or rule problem in the firewall. Linux just won't communicate over that route.

I can do an MTR <remote IP address> and the system pings as far as the firewall but no further. Tracert from a windows box on the same address works all the way to remote address.

I'm at a loss.

---

### Post by getut on 2010-03-13
Bump... anyone know where to start troubleshooting this?

---


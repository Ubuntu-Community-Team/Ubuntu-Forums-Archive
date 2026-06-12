---
title: "router dhcp server function query"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by intermentals on 2010-01-17
ver:9.10

if my router has it's dhcp server function activated how do make my server assign licenses instead?

I'm thinking I'd just turn off the function and host the router in the dhcpd.conf file but am unsure of how to do this

thanks

---

### Post by Iowan on 2010-01-17
Which router? (Brand, model,...)

I did something similar - my modem is capable of DHCP, but I disabled it and let my server run DNSmasq for DNS/DHCP server.

---


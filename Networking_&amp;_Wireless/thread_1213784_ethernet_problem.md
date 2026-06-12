---
title: "ethernet problem"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by gokhancapar on 2009-07-15
Hi,

I have two ethernet cards, eth0 and eth1 and a DHCP server.

eth0 cannot aquire an ip and fails, eth1 then gets and ip and works fine.

but if I disable eth0 in /etc/network/interfaces then eth1 still gets an ip but cannot reach internet. It can only ping local computers.

I have unplugged eth0 but still etc networking sees it as a working device and in order to get eth1 working correctly eth0 has to fail for getting an ip from dhcp.

Does anyone have a clue, what may be the problem?

Thanks...

---


---
title: "multiple default gateways from multiple DNS servers"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by duane-tech on 2009-10-14
2 network interfaces -- both use DHCP, both DHCP servers assign a default gateway.
I end up with 2 default entries in my routing table.

How can I ensure that only 1 default gateway is created?

The second interface is activated using laptop-net. It runs whenever eth0 the connection changes. 
I don't want to have the second DHCP server not issue a gateway in case the first interface is down, so the logic has to be done on the laptop.

---


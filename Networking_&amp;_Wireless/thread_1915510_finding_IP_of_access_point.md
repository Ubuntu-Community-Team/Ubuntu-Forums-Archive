---
title: "finding IP of access point"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by AstroLlama on 2012-01-26
Bed and breakfast with 2 floors has the following LAN setup:

Modem --> switch --> wifi router and AP 1 --> wifi AP 2

Everything is working fine, but I don't know the IP address given to AP 1 or AP 2. It used to be 192.168.0.2 and 192.168.0.3 but now modem's DHCP server is different. 

modem IP: 192.168.**1**.1
AP 1  IP: ??
AP 2  IP: ??

if i understand correctly AP 1 and 2 should not be working if they are still configured in the old DHCP range ending with 0.x. But network DOES WORK.

"If it ain't broke, don't fix it" but we need to change essid and passwords of AP 1 and 2 but are unable to without the IP addresses to acces the admin pages! any suggestions on how to discover the IPs of these two boxes?

---

### Post by SeijiSensei on 2012-01-26
Just connect a laptop to one of the router's ethernet ports.  You should be able to access the router's management page that way.

---


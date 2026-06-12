---
title: "Installing 2 Network Cards"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by nformosa on 2005-12-14
Hi All,

I have two questions:

1. I have installed Ubuntu 5.10 (base system only) with only 1 network card and now i would like to add a new network card (thus making it two on the machine). This is because we have to internet connection on our webserver and i would like to get through to both.

2. How can i configure the system that if i receive a request on port 80 from eth0 it will be sent back through the same nic and same goes for eth1!


Thansk for your time and patience
Nick

---

### Post by mlomker on 2005-12-15
That should be pretty much automatic as long as the network addresses are in different ranges.  

You'll want to specify an address on the card pointing toward your internal network rather than use DHCP.  You only want to have a gateway address set on the one pointing toward the Internet (if that card uses DHCP then it'll do that  automatically).

---


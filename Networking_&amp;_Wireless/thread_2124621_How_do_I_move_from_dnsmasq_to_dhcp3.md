---
title: "How do I move from dnsmasq to dhcp3?"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by dougsymes on 2013-03-11
I inherited a network that is running bind and unbound for DNS and dnsmasq for DHCP.  I want to move it to dhcp3 and drop dnsmasq.  Can anyone tell me the steps to make this as smooth as possible?  I went ahead and changed the lease length from 24 hours to 240 hours to buy some time.  Not only do I want to move DHCP but I also want DNS and DHCP to work as optimally as possible and with as little manual steps as possible related to the setup of any new client windows PC's.

---

### Post by Lars Noodén on 2013-03-11
Are the machines using dnsmasq for only DHCP, if so what options are set?  Are they using any other functions like caching?

---


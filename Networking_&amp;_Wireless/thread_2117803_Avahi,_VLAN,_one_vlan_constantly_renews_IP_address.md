---
title: "Avahi, VLAN, one vlan constantly renews IP address."
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Fatal0E on 2013-02-19
We have setup 12.04 with avahi and vlan at three buildings.  They are setup for two vlans, two are using vlans 2 and 100, one is using vlans 2 and 3.  

These have been working and providing the desired functions for about a week.  It was noticed this morning on the Windows Server 2008 DHCP logs that all three computers are constantly renewing the dhcp address on vlan 2.  Vlans 3 and 100 are working properly.  The renew is happening in as little as every six seconds.

Any suggestions as to why this would be happening?  I can set them static, but I am curious what is going on.

---


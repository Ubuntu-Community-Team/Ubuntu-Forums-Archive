---
title: "Can't get IP address on eth0"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by uberprik on 2010-07-01
Since my upgrade to 10.04 I can't use my eth0 wired connection.  The wireless works fine.  I have tried auto eth0 in network connections set to manual and dhcp.  eth0 shows up in ifconfig but no address is assigned.

Thanks

---

### Post by jonobr on 2010-07-01
When you set it to manual I guess you set it to a static IP.

When you changed it, did it show up in ifconfig?
If it didnt thats really odd.

In DHCP< did you try to make it ask for an IP address.
Open a terminal and then type

sudo dhclient

this will make it ask for an IP address again.

However, if you defined a static IP address and it didnt bind, thats pretty weird

---


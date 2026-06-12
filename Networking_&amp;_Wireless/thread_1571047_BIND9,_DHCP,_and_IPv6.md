---
title: "BIND9, DHCP, and IPv6"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by annoyingrob on 2010-09-09
I have a 10.04 server running that handles routing, DHCP, and DNS for my home network, which has been running flawlessly. Whenever a new host connects to the network, their name is added into the forward and reverse DNS zones, and everything is great. Recently, I've also set the server up to tunnel IPv6, and am using Radvd on it to announce IPv6 addresses to machines on my network. This also works perfectly, allowing all my machines IPv6 access to the internet.

Now, the problem. Obviously the DHCP server won't add AAAA records to BIND for the IPv6 addresses as it has nothing to do with them. If I add them manually, then any time that the DHCP server tries to update the DNS entry, it complains that it already exists, and does not match (because of the AAAA entry), then fails to update.

Is there some way to turn off this checking? Is there a better way to automatically populate the DNS with AAAA records other than manually entering them (short of DHCPv6)?

---


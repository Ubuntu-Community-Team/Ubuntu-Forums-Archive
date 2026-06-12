---
title: "How can I list connected wireless clients?"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by sjokomunn on 2009-01-20
Hey folks,

I've got an 8.04 server box set up as a gateway/firewall/wifi-router using hostapd, dhcp3-server and shorewall. I'm wondering if there's a command or simple script I can use at the command line to list connected clients along with their MAC and assigned IP. Any insight would be appreciated as always. Cheers.

-sjoko

---

### Post by steeleyuk on 2009-01-20
arp -a

Will display hostname, MAC address & IP of all hosts on the network.

---

### Post by sjokomunn on 2009-01-20
Presto! Thanks for the quick reply.

---


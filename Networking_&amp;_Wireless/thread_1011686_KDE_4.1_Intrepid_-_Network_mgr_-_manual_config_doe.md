---
title: "KDE 4.1 Intrepid - Network mgr - manual config doesn't work"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by Malibyte on 2008-12-15
Title pretty much explains it.  I have a "Home Wired" connection profile set up with a manually-set IP address, gateway, netmask, DNS servers and search domain for eth0.

However, it always comes up with a DHCP-obtained IP address, whether I check the "auto-connect" box or not, and if I try to reconnect after the machine's already up, nothing happens.

Someone has filed a bug report on this, and supposedly it was fixed - but, it wasn't....?

Anyone got this working (without manually modifying /etc/network/interfaces - this is a laptop)?

TIA
Bob

---

### Post by 316097 on 2008-12-15
Actually I noticed the same thing yesterday, I was going to convert all my boxes from DHCP to static ip-addresses, but it didn't work.

---


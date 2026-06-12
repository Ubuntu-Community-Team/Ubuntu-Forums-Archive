---
title: "Network manager connected to LAN + umts modem"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by E.Hyde on 2010-03-03
Hi to all guys,

i'm encountering an issue related to the connection at private lan (without an internet access) and the umts modem allowing me to reach internet.

I'm using Network Manager and Ubuntu 9.10 Desktop ed.

If i want to connect with umts modem i need to disconnect the lan, but not viceversa. It seems that lan has a priority, so when i'm connect to umts modem i can surf through the lan, but i'm not able to surfing the web.

I checked teh routing table, and when both connections are active i have 2 default gateways..

Any ideas?

---

### Post by E.Hyde on 2010-03-04
Solved!

Just setting "Use this connection only for resource on its network", under IpV4 routes of my lan connection, in the Network Manager.

---


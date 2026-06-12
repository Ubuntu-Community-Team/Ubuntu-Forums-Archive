---
title: "getting WinXP behind Dapper gateway to access internet"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by troypiggo on 2006-06-04
I have a network with my ADSL router (192.168.1.1) connected to Dapper machine (eth0 192.168.1.10), and the Dapper machine (eth1 192.168.0.1) connected to WinXP machine (192.168.0.3).

Dapper can connect to internet fine, and can connect to WinXP fine.
WinXP can connect to Dapper fine, but can't connect to internet :-(

This was working last week when the gateway machine was Breezy, but when I did a clean install of the Dapper server release it no longer forwards packets.

Same rules in iptables as before, and edited /etc/sysctl.conf to allow packet forwarding, restarted networking etc.

WinXP has 192.168.0.1 as it's default gateway, but can't even ping Dapper's other NIC 192.168.1.10.
Dapper has 192.168.1.1 as it's default gateway, but as I said it's working fine.

Any ideas?  If you have this working can you print your route output?

---

### Post by troypiggo on 2006-06-06
Turned out to be an error in WinXP's routing table. Flushed it with "route -f" and all good now.

---


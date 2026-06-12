---
title: "sd and sr drivers"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2009-10-28
When I run sudo cat /var/log/dmesg | grep -i eth I get the following;

[    1.753614] Driver 'sd' needs updating - please use bus_type methods
[    1.753626] Driver 'sr' needs updating - please use bus_type methods
[    2.834283] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.124246] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[   39.600864] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.633086] e1000: eth1: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   39.633378] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   43.965494] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

What is necessary of fix this?

---


---
title: "Network Manager display wrong speed"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-04-11
Hi,

Using Ubuntu 8.10 x64, system up to date.

I currently have some cabling quality issue. The computer cannot autonegotiate at 100 Mbps. And ended up being disconnected. So I forced to 10 Mbps by
```
sudo ethtool -s eth0 speed 10 duplex full autoneg off
```
After that, the connection is OK. When I right click the NM icon (on top right panel), select Connection Information. The speed says "100 Mb/s"

If I do ```
sudo ethtool eth0
``` the output says Speed = 10 Mb/s. Does the Network Manager notification display static info gathered at boot time and never refresh the real values?

---


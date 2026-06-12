---
title: "3c59x turn auto negotiation off 8.10?"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by mrhaffer on 2009-01-08
Been trying to get 8.10 wired connection to work.  Old PC 750r, cyclone rev 24 internet card.  Tried deleting network manager and configuring card with /etc/network/interfaces, static interface, media 10baseT/Half.  Dual boot with windows 98 where card works.  

Once I ran windows.  Unplugged network and started ubuntu. lshw -C network showed 10MB/sec autonegotiation=off and I did a hotplug and was finally able to ping my router and network but not get internet.  Eversince I always have autonegotiation on and when I hotplug the connection changes to 100MB and I can only ping 127.0.0.1.

Since I don't have an internet connection, I can't load ethtool which I think I used on a previous version.  I reinstalled 8.10 and have the network manager back.  Anyway to adjust card parameters with the original install?

Could I download a ethtool tar.gz file and transfer it to synaptic Program Manager somehow.

Thanks


Answer:  Mii-tool is part of 8.10 install.  Command is sudo mii-tool -F 10baseT-HD eth0 [zero]  Forces 10mb and turnsoff autoneg.  Now have internet with network manager.  Can't believe how much time I spent on this.

---


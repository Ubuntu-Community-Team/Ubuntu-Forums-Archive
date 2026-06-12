---
title: "Having hard time to connect to my Wireless Network"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by amjjawad on 2012-11-01
Hi,

I hope chili555 or Wild Man will see this :D

Ok, this laptop is driving me crazy.

This is Lenovo G570 Core i5 2nd generation with 4GB RAM.
Dual-Boot (Windows 7 and Lubuntu 12.04).

[**I had previously an issue**]("http://ubuntuforums.org/showthread.php?t=1643545") on a different machine and different Wireless Adapter and chili555 helped me and fixed it.

I will explain what is wrong:

Whenever I disconnect my Wireless Network, I can not re-connect back UNLESS I restart the Range Extender outside my room.

Before I do that, I try to:
a- Disable then Enable Networking (right click on the Network Manager icon, uncheck Enable Networking and recheck it back).

b- Delete the Network and re-add it again

c- Log off and Reboot

ALL the above 3 steps will never fix the issue UNLESS I reboot the Range Extender outside and sometimes, I have to do it twice.

As long as I'm connected to the Wireless Network, everything is fine. Once I disconnect it, I'm in trouble.


What makes this issue weird and confusing to me is:
This very machine has two systems as I mentioned before (Windows 7 and Lubuntu 12.04). With Windows 7, it is connecting to the Wireless Network like a charm.

What makes it even more strange is each and every device at my room is connected at the same time my laptop WHILE ON LUBUNTU is NOT. So, the Range Extender is FINE and there is something wrong elsewhere.

```
*-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: b8:70:f4:36:93:f8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d0500000-d053ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:d8:aa:5d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-32-generic firmware=N/A ip=192.168.2.21 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0400000-d040ffff

``` 

I have added this:
```
SUSPEND_MODULES="ath9k"
```
As per [these instructions]("http://ubuntuforums.org/showpost.php?p=10983947&postcount=5") by chili555.

But that is not helping.

Thank you!

---

### Post by amjjawad on 2012-11-04
No reply yet!

I have noticed that when I disconnect my laptop from one network in Room A and go to Room B and use another network, the stupid Network Manager keeps trying to connect to the previous network at Room A even though it is out of range or the signal is poor. Perhaps this is the problem? I'm not sure. I mean, it keeps trying for some weird reason to connect to the previous network and refusing to connect to the new network which has the strongest signal and closer!

I'm stuck for the last 10mins now as the Network Manager is keep trying to connect to the closest network that has the better signal. I'm using my other machine to post this.

In Windows 7 on the same machine, the process is much smarter + faster and I do hate to say this but this is true. 

I'm still waiting for some help/answers/thoughts/etc :)

---


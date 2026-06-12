---
title: "Network Speed"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by rahbz on 2012-01-06
Hi,
My device works perfectly fine but I need to increase the network speed. These are the outputs of the commands of following
-----------
rahbz@game:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
------------
rahbz@game:~$ dmesg | grep -e eth0 -e bcm
[ 3.394519] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xffffc90000674000, 64:31:50:62:91:24, XID 083000c0 IRQ 41
[ 18.043216] r8169 0000:03:00.0: eth0: link down
[ 18.043222] r8169 0000:03:00.0: eth0: link down
[ 18.043540] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 19.876554] r8169 0000:03:00.0: eth0: link up
[ 19.876893] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 30.530903] eth0: no IPv6 routers present
[ 2787.217234] r8169 0000:03:00.0: eth0: link down
[ 2788.897083] r8169 0000:03:00.0: eth0: link up
[ 2793.541536] r8169 0000:03:00.0: eth0: link down
[ 2839.887070] r8169 0000:03:00.0: eth0: link up
[ 2850.019417] eth0: no IPv6 routers present
------------
rahbz@game:~$ cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory
--------------
rahbz@game:~$ lshw -C Network

*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 03
serial: 64:31:50:62:91:24
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=off broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=10.109.51.117 latency=0 multicast=yes port=MII speed=100Mbit/s
resources: irq:41 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff memory:c1410000-c141ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
-------------
rahbz@game:~$ sudo ethtool eth0
[sudo] password for rahbz: 
Settings for eth0:
Supported ports: [ TP MII ]
Supported link modes: 10baseT/Half 10baseT/Full 
100baseT/Half 100baseT/Full 
1000baseT/Half 1000baseT/Full 
Supports auto-negotiation: Yes
Advertised link modes: Not reported
Advertised pause frame use: No
Advertised auto-negotiation: No
Speed: 100Mb/s
Duplex: Full
Port: MII
PHYAD: 0
Transceiver: internal
Auto-negotiation: off
Supports Wake-on: pumbg
Wake-on: g
Current message level: 0x00000033 (51)
drv probe ifdown ifup
Link detected: yes
---------------
I used the command ethtool -S eth0 speed 1000 duplex full autoneg on even on that my network settings are remained to 100Mbps network speed.
what can be the problem and please give me a solution. After seeing all these commands I think my lappy supports 1gbps network.

---

### Post by papibe on 2012-01-06
Does you router supports 1gbps? In order to have gigabit transfers between machines, your router has to support it.

Just a thought.
Regards.

---

### Post by rahbz on 2012-01-06
Yes, my router supports gigabyte transfer. I use cat.6 lan wire to connect to the router.

---


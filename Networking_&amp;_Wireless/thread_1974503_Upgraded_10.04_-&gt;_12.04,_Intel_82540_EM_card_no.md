---
title: "Upgraded 10.04 -&gt; 12.04, Intel 82540 EM card not working"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by farazk on 2012-05-06
Logs are  as follows :

**sudo lshw -C network**
  *-network
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:04:03.0
       logical name: eth1
       version: 02
       serial: 00:07:e9:10:b9:8d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI firmware=N/A ip=192.168.4.21 latency=32 link=yes mingnt=255 multicast=yes port=twisted pair
       resources: irq:20 memory:d0440000-d045ffff memory:d0420000-d043ffff ioport:d000(size=64) memory:d0400000-d041ffff


**dmesg | grep -i eth1**
[    1.396161] e1000 0000:04:03.0: eth1: (PCI:33MHz:32-bit) 00:07:e9:10:b9:8d
[    1.396166] e1000 0000:04:03.0: eth1: Intel(R) PRO/1000 Network Connection
[   16.743580] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.183675] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.184033] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   18.184820] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   18.185343] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   20.189059] e1000 0000:04:03.0: eth1: Detected Tx Unit Hang
[   22.192215] e1000 0000:04:03.0: eth1: Detected Tx Unit Hang
[   24.196231] e1000 0000:04:03.0: eth1: Detected Tx Unit Hang
[   26.200193] e1000 0000:04:03.0: eth1: Detected Tx Unit Hang
[   28.204152] e1000 0000:04:03.0: eth1: Detected Tx Unit Hang
[   28.768016] eth1: no IPv6 routers present
[   28.832034] NETDEV WATCHDOG: eth1 (e1000): transmit queue 0 timed out
[ 1682.928021] eth1: no IPv6 routers present
[ 2413.520021] eth1: no IPv6 routers present

---

### Post by praseodym on 2012-05-06
Remove the package "resolvconf", if installed.

---

### Post by farazk on 2012-05-06
Thanks a lot, it is working now. Can you please explain the reasons behind this ?

---

### Post by praseodym on 2012-05-06
Ubuntu (obviously since 12.04) builds up a local DNS cache, therefore 127.0.0.1 is listed in the /etc/resolv.conf, not the nameservers of your ISP or the router IP. Obviously this doesnt work properly.

---


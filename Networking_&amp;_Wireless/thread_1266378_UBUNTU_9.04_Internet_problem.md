---
title: "UBUNTU 9.04 Internet problem"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by Chetan26 on 2009-09-14
Hi ,
    I have recently  installed ubuntu 9.04 on my desktop with 2 n/w cards.
    The problem is  after installation of Ubuntu 9.04 on starting the machine every time the  OS is switiching the  Ethernet cards.
   
    As  eth0 once, eth2  once and eth2 next  . Due to this  iam not able to access  internet and even system is  not  shown in the network.

Could you  pls suggest a way that every time I reboot  it defaults to eth0.


Many Thanks
Chetan

---

### Post by overdrank on 2009-09-14
Moved to  Networking & Wireless

---

### Post by Iowan on 2009-09-14
Is it changing the definition in **lshw -C network**?
 Does it change what's in */etc/udev/rules.d/70-persistent-net.rules*?

---

### Post by Chetan26 on 2009-09-17
Hi , 
    When I run the command lshw -C.
    I get the  folowing o/p. 


root@8pmserver1:/home/serveradmin# lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:16:00.0
       logical name: eth2
       version: 12
       serial: 00:10:18:42:0d:8e
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=1.8.1 firmware=1.9.3 ip=192.168.1.200 latency=64 link=no mingnt=64 module=bnx2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:1a:00.0
       logical name: eth0
       version: 21
       serial: 00:1a:64:a3:d3:1a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5721-v3.65, ASFIPMI v6.20 ip=192.168.1.204 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:1b:00.0
       logical name: eth1
       version: 21
       serial: 00:1a:64:a3:d3:1b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5721-v3.65, ASFIPMI v6.20 ip=192.168.1.202 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:64:f9:5d:9d:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



can you  pls analyse these  results  and let me know  wats happening?


Thanks
Chetan

---


---
title: "Emulex LP10000 installation problem"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by AlexZiX on 2012-06-25
Hi.

I have some servers under Ubuntu Server 11.04. It's main info about one of my servers:

Operating system	Ubuntu Linux 11.04
Kernel and CPU	Linux 2.6.38-15-generic-pae on i686
Processor information	Intel(R) Xeon(TM) CPU 3.00GHz, 4 cores

At the last week I've bought HBA adapters for gigabit fiber optical network Emulex LP10000. I spent all my time at last week but can't run this device as newtwork card. Server see that card exists:

root@BazFTP:~# dmesg | grep Emulex
[    1.265703] Emulex LightPulse Fibre Channel SCSI driver 8.3.20
[    1.265708] Copyright(c) 2004-2009 Emulex.  All rights reserved.

But not as network card:

root@BazFTP:~# lshw -C network
  *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:18:71:e4:81:9c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5704-v3.26, ASFIPMIc v2.25 ip=192.168.158.98 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:25 memory:fdef0000-fdefffff
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2.1
       bus info: pci@0000:02:02.1
       logical name: eth1
       version: 10
       serial: 00:18:71:e4:81:9b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5704-v3.26 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:26 memory:fdee0000-fdeeffff

LPFC driver loaded:

root@BazFTP:~# lsmod | grep lpfc
lpfc                  476876  0
scsi_transport_fc      52205  3 fcoe,libfc,lpfc

Any ideas why it doesn't work?

---


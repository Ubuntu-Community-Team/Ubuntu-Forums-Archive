---
title: "Silicom Dual port Copper Giga Ethernet issues"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by GlitchEXE on 2009-10-04
I'm trying to setup a snort sensor from an old box.  So far everything has gone good, installed ubuntu and snort communication to central server is all setup, however when I try to run the command
```
sudo ifconfig eth2 up
```
I'm greeted with the response
> eth2: ERROR while getting interface flags: No such device

I've run an lspci -nn command and was given the following:
```
00:00.0 Host bridge [0600]: Intel Corporation E7520 Memory Controller Hub [8086:3590] (rev 0c)
00:02.0 PCI bridge [0604]: Intel Corporation E7525/E7520/E7320 PCI Express Port A [8086:3595] (rev 0c)
00:04.0 PCI bridge [0604]: Intel Corporation E7525/E7520 PCI Express Port B [8086:3597] (rev 0c)
00:05.0 PCI bridge [0604]: Intel Corporation E7520 PCI Express Port B1 [8086:3598] (rev 0c)
00:06.0 PCI bridge [0604]: Intel Corporation E7520 PCI Express Port C [8086:3599] (rev 0c)
00:07.0 PCI bridge [0604]: Intel Corporation E7520 PCI Express Port C1 [8086:359a] (rev 0c)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
01:00.0 PCI bridge [0604]: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A [8086:0329] (rev 09)
01:00.1 PIC [0800]: Intel Corporation 6700/6702PXH I/OxAPIC Interrupt Controller A [8086:0326] (rev 09)
01:00.2 PCI bridge [0604]: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B [8086:032a] (rev 09)
01:00.3 PIC [0800]: Intel Corporation 6700PXH I/OxAPIC Interrupt Controller B [8086:0327] (rev 09)
02:01.0 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
02:01.1 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
02:03.0 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
02:03.1 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
03:01.0 RAID bus controller [0104]: LSI Logic / Symbios Logic MegaRAID [1000:1960] (rev 01)
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express [14e4:1659] (rev 11)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express [14e4:1659] (rev 11)
07:00.0 PCI bridge [0604]: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A [8086:0329] (rev 09)
07:00.1 PIC [0800]: Intel Corporation 6700/6702PXH I/OxAPIC Interrupt Controller A [8086:0326] (rev 09)
07:00.2 PCI bridge [0604]: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B [8086:032a] (rev 09)
07:00.3 PIC [0800]: Intel Corporation 6700PXH I/OxAPIC Interrupt Controller B [8086:0327] (rev 09)
08:01.0 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
08:01.1 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
08:02.0 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
08:02.1 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
09:01.0 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
09:01.1 Ethernet controller [0200]: Silicom Ltd. Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter [1374:0029] (rev 03)
0a:01.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL [1002:4752] (rev 27)
```

The Broadcom Gigabit NICs are working, so it looks like the Silicom adapters are the issue, and I can't for the life of me find a driver that will allow these to start.

I've looked at another device running Redhat with
```
ethtool -i eth2
```
and it tells me it's
> driver: e1000bp
version: 5.6.10.1.silc.3.19-NAPI
firmware-version: N/A
bus-info: 08:01.1

But I can't for the life of me find an e1000bp driver for Ubuntu.

UPDATE:
I've run the *lshw -C Network* command and come up with the following as well:
```
ipcuser@ipc-lpids-s2:~$ sudo lshw -C Network
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 1.1
       bus info: pci@0000:02:01.1
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 3.1
       bus info: pci@0000:02:03.1
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 11
       serial: 00:30:48:79:84:0a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5721-v3.29a, ASFIPMI v6.09 ip=10.110.1.142 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 11
       serial: 00:30:48:79:84:0b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=half firmware=5721-v3.29a, ASFIPMI v6.09 latency=0 link=yes module=tg3 multicast=yes port=twisted pair
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 1
       bus info: pci@0000:08:01.0
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 1.1
       bus info: pci@0000:08:01.1
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:2 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:3 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 2.1
       bus info: pci@0000:08:02.1
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 1
       bus info: pci@0000:09:01.0
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Silicom Dual port Copper Giga Ethernet 546GB Bypass Server Adapter
       vendor: Silicom Ltd.
       physical id: 1.1
       bus info: pci@0000:09:01.1
       version: 03
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list
       configuration: latency=52 mingnt=255
```

So no drivers are claiming the Silicom Adapters

Any thoughts?

---

### Post by GlitchEXE on 2009-10-07
I was finally able to contact the manufacturer and built a driver that way.  Shame that they don't openly post it online.

---


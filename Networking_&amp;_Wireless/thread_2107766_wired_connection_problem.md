---
title: "wired connection problem"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by Ax3 on 2013-01-22
Hi I have Dell mini 1012 I want to use Ubuntu as the main OS. I’m using w7 starter . now I had downloaded 12.10 but found no wired or wireless connection . I make several try but useless . plz check

sudo gedit /etc/modprobe.d/blacklist.conf
blacklist r8169
sudo update-initramfs -u
tar jxvf r8101-1.022.00.tar.bz2
cd r8101-1.022.00
sudo sh autorun.sh
Then make restart and the problem still, and made

sudo /etc/init.d/networking restart
but no news

this some output

3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
$ dmesg | grep -i eth0
[ 1.505805] eth0: Identified chip type is 'RTL8103E'.
[ 1.505816] eth0: RTL8101E at 0xf8424000, 00:26:b9:ea:c9:72, IRQ 16
[ 13.475968] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 16.229691] r8101: eth0: link down
[ 16.248957] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 16.251098] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 17.800307] r8101: eth0: link up
[ 17.800944] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes read
$ sudo modprobe rtl8723e
[sudo] password for hany:
**`FATAL: Module rtl8723e not found.
$ sudo lshw -c network
*-network description: Ethernet interface

product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0\
version: 02
serial: 00:26:b9:ea:c9:72
size: 100Mbit/s
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.022.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:16 ioport:2000(size=256) memory:f0f20000-f0f20fff memory:f0f10000-f0f1ffff memory:f0f40000-f0f5ffff

*-network

description: Network controller
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:07:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:17 memory:f0100000-f0103fff
plz help me how to clear this problem no wired or wireless connection , plz tel me in details , i'm still new usre

---


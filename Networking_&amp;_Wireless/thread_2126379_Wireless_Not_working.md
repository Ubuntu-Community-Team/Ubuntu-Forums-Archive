---
title: "Wireless Not working"
date: 2013-03-16
forum: Networking &amp; Wireless
---

### Post by tejaswinip on 2013-03-16
I am running Ubuntu 64 bit 12.04 3.2.0-37-generic. My wireless is not working.

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

 I tried running rfkill unblock all. But that did not fix it.


 lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 2c:76:8a:db:85:d6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=128.59.13.148 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network DISABLED
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:ac:0f:34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-37-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:2000(size=256) memory:d4400000-d4403fff



I tried several threads on ubuntu forum already but was not of much help. Could you please help me fix it

---


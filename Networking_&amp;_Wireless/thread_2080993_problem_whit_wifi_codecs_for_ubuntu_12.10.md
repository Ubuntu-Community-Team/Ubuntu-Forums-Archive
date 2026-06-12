---
title: "problem whit wifi codecs for ubuntu 12.10"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by alecst on 2012-11-05
Hello, I have problem with the wifi connexion: in ubuntu 12.10 I need driver for my wifi on notebook toshiba c850-a986 . Please help me because I'm total new in ubuntu os...I gues that is realtek manufactured but I can't see nothing under  ubuntu :(

root@ubuntu:~# sudo lshw -C network -numeric
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd. [10EC:8723]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:92400000-92403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10EC:8136]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 4c:72:b9:5f:d5:9e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:90004000-90004fff memory:90000000-90003fff

I try questions 163141 but don't work for me.
[http://askubuntu.com/questions/163141/drivers-for-realtek-wireless-module-for-toshiba-c850-a965](http://askubuntu.com/questions/163141/drivers-for-realtek-wireless-module-for-toshiba-c850-a965)

---


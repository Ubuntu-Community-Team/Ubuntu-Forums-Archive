---
title: "my wifi card doesn't work for other applications ,work only with built in application"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by imad_el_kholti on 2013-08-09
hello .


i installed ubuntu 13.04 two weeks ago and had problem with the wifi card ,therewas no driver for it , so i used the additional driver (proprietary) .


worked just fine . lately i wanted to use radar wifi , i installed it and when i tryed start it , the wifi's driver blocked . and when i tryed restart th pc , doesn't shutdown , the ubuntu logo was shown for long time tell i  power it off with long press on power button 


here is some infos


ubu@ubu-Inspiron-3520:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: 08:ed:b9:92:32:7b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:f7c00000-f7c07fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: e0:db:55:8e:83:7e
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wwan0
       serial: 02:50:f3:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes

---


---
title: "wifi problem after the driver updates"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by bou3lam on 2013-02-10
hi
please help, my wifi connection has become very slow and unstable after the last wl driver updates, if i understand is a major problem for many, the speed is very slow and sometimes when i access the router admin panel its give me 400 error page, sometimes i must disable and re-enable wifi (button in f12) to get connected, under windows wifi is working very good

ubuntu 12.04

 *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.4 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:16 memory:c2500000-c2503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes



 iwconfig
lo        no wireless extensions.

wwan0     no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"SAGEM_FA54"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 9E:37:EB:R7:78:68   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

---


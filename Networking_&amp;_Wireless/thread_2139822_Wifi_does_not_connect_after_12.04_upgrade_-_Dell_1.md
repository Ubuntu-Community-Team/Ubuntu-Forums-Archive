---
title: "Wifi does not connect after 12.04 upgrade - Dell 1749"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by wutwutisay on 2013-04-27
Hello,

I have a Dell 1749 and was using 11.10 on ethernet and wireless with no issues. I recently upgraded to 12.04 LTS and the wifi has stopped working. The ethernet works fine. The wifi shows up the networks around but tries to connect to a network forever, re-prompting me for the password every few seconds without any progress. Please help me out.

sudo lshw -C network produces:

```
*-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 70:f1:a1:e7:67:8f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-40-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:ed:d3:41
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=//redacted// latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:5000(size=256) memory:f8404000-f8404fff memory:f8400000-f8403fff memory:f8420000-f843ffff


```

From what I can tell this seems to be a common problem with Broadcomm cards. I've tried a bunch of solutions off askubuntu and results from this forum but nothing seems to work. Please help me out.

---


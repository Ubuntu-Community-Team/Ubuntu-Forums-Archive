---
title: "Realtek RTL8191SEvB always turned off"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by jefft255 on 2013-04-13
I deleted windows from my computer and installed Ubuntu, now the key used for activating/deactivating my wifi card doesnt work. It is tuned off and I have no idea how to turn it on. I am using a Thinkpad Edge 13.

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by jefft255 on 2013-04-13
first one:

  ```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:26:9e:f5:b6:a1
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.0.103 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:42 ioport:a000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network DISABLED
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 00:26:5e:ed:e3:2c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.5.0-27-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:b000(size=256) memory:d0300000-d0303fff



second one:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

---


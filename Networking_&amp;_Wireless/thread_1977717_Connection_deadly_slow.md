---
title: "Connection deadly slow"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by endamaco on 2012-05-10
Hi to all, I'm currently under 11.10 and since a lot of time (and through a couple of updates) my wifi (only under ubuntu, in windows it's all ok) it's very very slow. Ping it's all ok, problems are only while browsing (chrome, chromium, firefox all the same).
Do you have any idea?

**iwconfig**
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Collautti"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:3F:42:0A:0A   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:202  Invalid misc:2081   Missed beacon:0

```

**lshw -c network**
```
*-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:a3:8f:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-17-generic firmware=8.83.5.1 build 33692 ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:de200000-de201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ff:49:1a
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:6000(size=256) memory:d4010000-d4010fff memory:d4000000-d400ffff memory:d4020000-d402ffff
```

---


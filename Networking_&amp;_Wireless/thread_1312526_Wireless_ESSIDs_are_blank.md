---
title: "Wireless ESSIDs are blank"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by fundae on 2009-11-03
I'm trying to connect to a local WiFi network, but Network Manager doesn't show the network name. When I run sudo iwlist eth1 scan, I get the following:

> ```
eth1      Scan completed :
          Cell 01 - Address: 00:14:6A:B2:2B:F0
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:14:6A:B2:20:50
                    ESSID:""
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:14:6A:B2:15:60
                    ESSID:""
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:14:6A:B2:31:40
                    ESSID:""
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


```

Here is the output of sudo lshw -C network:
> ```
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:9a:7b:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:9f:73:1f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.16.31.20 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:4000(size=256) memory:f8610000-f8610fff(prefetchable) memory:f8600000-f860ffff(prefetchable) memory:f8620000-f862ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Can anyone please help? Why are these network shown without names? What can I do to try and fix the problem?

---


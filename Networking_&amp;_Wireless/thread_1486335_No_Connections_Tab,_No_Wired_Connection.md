---
title: "No Connections Tab, No Wired Connection"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by Bungo Pony on 2010-05-17
Fresh install of UbuntuStudio 10.04. This is really bizarre. I can't seem to connect to the wired connection mainly because there is no connections tab (pic attached). Here's some printouts:

dmesg:
```
[    2.542325] 8139too Fast Ethernet driver 0.9.28
[    2.598068] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[3]  MMIO=[ec000000-ec0007ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[    2.602257] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[    2.604179] eth0: RealTek RTL8139 at 0x8c00, 00:90:f5:17:24:ba, IRQ 5
[  135.466356] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  146.248029] eth0: no IPv6 routers present


```

lshw -C network:
```

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:17:24:ba
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=127.0.0.1 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:5 ioport:8c00(size=256) memory:ec005000-ec0050ff
```

Any help would be appreciated.

---

### Post by Bungo Pony on 2010-05-17
bump

---

### Post by Bungo Pony on 2010-05-18
It looks as if I've found the problem...

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/566811](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/566811)

The help documents all refer to the Connections tab, but it was intentionally removed in Lucid. 

Network-manager has been removed because it was causing problems with latency. So there seems to be some kind of conflict as to what should be used to configure connections:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/570828](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/570828)

In other words, it's nothing I screwed up, but what the devs screwed up. If I can't hack it to work, I'll be back in Hardy at least on this machine.

---

### Post by cariboo on 2010-05-19
What happens if you open a terminal and type:

```
sudo dhclient eth0
```

---


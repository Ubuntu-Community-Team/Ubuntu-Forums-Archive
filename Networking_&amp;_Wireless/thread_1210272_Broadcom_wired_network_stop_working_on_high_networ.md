---
title: "Broadcom wired network stop working on high network load"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by jskasia on 2009-07-11
Hello there, I have a problem to ask. 

Broadcom wired Ethernet card stop working on high network load
such as coping within LAN network  

My laptop run with ubuntu 9.04 (32 bit)
kernel 2.6.28-13-generic

lspci -v result is:
```
08:09.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Fujitsu Limited. Device 123b
        Flags: bus master, fast devsel, latency 64, IRQ 20
        Memory at d4214000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
        Kernel driver in use: b44
        Kernel modules: b44

```

dmesg |grep b44 result is:
```
[    4.854253] b44 0000:08:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.928164] b44.c:v2.0
[   28.816181] b44: eth0: Link is up at 100 Mbps, full duplex.
[   28.816186] b44: eth0: Flow control is off for TX and off for RX.
[ 1196.011361] b44: eth0: powering down PHY
[ 1197.000347] b44: eth0: Link is down.
[ 1199.000220] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1199.000227] b44: eth0: Flow control is off for TX and off for RX.

```

Is there any work around for this problem?

Thanks

---


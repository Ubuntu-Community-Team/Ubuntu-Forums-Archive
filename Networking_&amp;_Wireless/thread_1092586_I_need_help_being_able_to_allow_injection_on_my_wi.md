---
title: "I need help being able to allow injection on my wireless card (bcm43)"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by thrasher6900 on 2009-03-10
I went to several sites and I've found ' patches ', however none were compatible with 2.6.27-13 kernel

I'm running intrepid and have a Compaq Presario c552. 

Here are my stats after running lspci -vv

I hope this helps.



```
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Hewlett-Packard Company Device 1363
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at 88000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: ssb, wl

08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (8000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 2000 [size=256]
    Region 1: Memory at d0100000 (32-bit, non-prefetchable) [size=256]
    Kernel driver in use: 8139too
    Kernel modules: 8139cp, 8139too
```

---

### Post by N04h on 2009-03-10
Are you sure your chipset supports injection?

---

### Post by thrasher6900 on 2009-03-11
> **N04h said:**
> Are you sure your chipset supports injection?It siad so  on the aircrack-ng site.

I just said something about the driver that comes with this OS doesn't include these capabilities and you have to some how patch them in.

---

### Post by thrasher6900 on 2009-03-13
um anybody . .....

---

### Post by thrasher6900 on 2009-04-02
My card does support injection according to the site.

Please help . .....

---


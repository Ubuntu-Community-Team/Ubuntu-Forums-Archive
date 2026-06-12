---
title: "Broadcom 43xx a different issue"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by fedebaka on 2013-04-27
I have an acer 5551 notebook and xubuntu raring, I'm having this issue which I think is different from all I found. When I boot, the wireless light is off, but the panel indicator says the network and the wireless are on, but no networks are found. Using the switch (fn+f3) turns on and off "wireless" in the panel indicator but not the wifi light. Only after a reboot, either from windows to ubuntu or from ubuntu to ubuntu, the light goes on and the wifi works.

All threads point to rfkill, but I have nothing locked according to rfkill:
```
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

But see what lspci says (-k -vvv):
```

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 036e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at f1100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tg3

08:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
    Subsystem: Foxconn International, Inc. T77H103.00 Wireless Half-size Mini PCIe Card
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f1000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
```

What's with that "access denied"? What can I do? Thanks!

---


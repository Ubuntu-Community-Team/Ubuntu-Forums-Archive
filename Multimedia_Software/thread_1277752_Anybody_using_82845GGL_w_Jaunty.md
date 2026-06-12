---
title: "Anybody using 82845G/GL w/ Jaunty?"
date: 2009-09-28
forum: Multimedia Software
---

### Post by Cuco3 on 2009-09-28
Has anyone with an 82845G/GL integrated video card been able to get it to work properly under Jaunty? The problems I'm experiencing are:

[LIST]
[*]Choppy video and scrolling
[*]When trying to enable desktop effects, it says they can't be enabled
[*]When I suspend (S3) then resume, the graphics flicker randomly.
[/LIST]

This is what "LSPCI -vv" revealed if it's of any use```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
    Subsystem: Intel Corporation Device 5352
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel modules: intelfb

```

---

### Post by diesch on 2009-09-28
Maybe you'll find some help in [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by Cuco3 on 2009-09-28
> **diesch said:**
> Maybe you'll find some help in [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")I tried that already, thanks anyways, diesch.

---


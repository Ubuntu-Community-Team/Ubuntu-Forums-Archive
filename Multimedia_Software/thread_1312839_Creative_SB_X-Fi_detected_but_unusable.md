---
title: "Creative SB X-Fi detected but unusable"
date: 2009-11-03
forum: Multimedia Software
---

### Post by antennen on 2009-11-03
Hello.

I just installed (x)Ubuntu 9.10 64bit on Saturday. Most things went smoothly except my sound card.

Relevant lspci -vv info:
```
00:09.0 Multimedia audio controller: Creative Labs SB X-Fi
        Subsystem: Creative Labs Device 0021
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at b000 [size=32]
        Region 1: Memory at f9800000 (64-bit, non-prefetchable) [size=2M]
        Region 3: Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Kernel modules: snd-ctxfi

```Related dmesg:
```
[   11.018407] SB-XFi 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.018412] SB-XFi 0000:00:09.0: PCI: Disallowing DAC for device
[   11.018415] architecture does not support PCI busmaster DMA with mask 0xffffffffffffffff
[   11.018420] SB-XFi 0000:00:09.0: PCI INT A disabled
[   11.018424] ctxfi: Something wrong!!!
```AlsaInfo: [http://pastebin.ca/1655009](http://pastebin.ca/1655009)

Even when disabling the via card manually through blacklisting, there is no difference. I am at loss what to do next. I've tried the AlsaUpdate script with no luck, forcing snd_ctxfi to load in /etc/modules doesn't do anything good either.

Thankful for all sorts of help,

antennen

---


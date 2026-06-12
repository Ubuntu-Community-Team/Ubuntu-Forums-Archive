---
title: "Poor video performance since recent X-update"
date: 2010-11-19
forum: Multimedia Software
---

### Post by fperwth on 2010-11-19
Hi,

I am running Kubuntu 10.10 on an Acer Aspire TimelineX 3820TG notebook, Intel i5-430M CPU with integrated graphics.

I had no problems until my last apt-get upgrade two days ago, when a whole bunch of x-related-packages were updated.

Since then, no fluent video playback is possible anymore (whole screen flickers black, Desktop becomes very slow) and the KDE desktop effects also became very slow and jerky. Fullscreen Video playback has become totally impossible. It seems like the hardware acceleration is completely gone.

Since the update, dmesg also is flooded with messages saying
```
intel ips 0000:00:1f.6: MCP power or thermal limit exceeded
```

Is there any way to "downgrade" to the previous X packages?
I am really annoyed that the update seems to be broken for me...

```
$ sudo lspci
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0365
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 44
        Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
        Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 4: I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4179
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a4] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: i915
        Kernel modules: i915
```

---


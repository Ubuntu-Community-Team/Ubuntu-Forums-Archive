---
title: "Lost sound when updated to kubuntu 6.06"
date: 2006-10-03
forum: Multimedia &amp; Video
---

### Post by hena on 2006-10-03
Hi,

I updated to kubuntu 6.06 from 5.10 and have lost sound completely. As far as I can tell the system detects my soundcard, but I don't hear anything (even the kde test sound button is silent). I checked kmix and there was no mutes on in master or pcm (I assume that sound is muted if the light is off).

Heres the listing from lspci -vvv from sound card
```
0000:00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4760 SBLive!
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at e000 [size=32]
        Capabilities: [dc] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

---


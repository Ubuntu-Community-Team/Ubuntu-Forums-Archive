---
title: "Which NVIDIA card is this?"
date: 2011-01-22
forum: Multimedia Software
---

### Post by boondocks on 2011-01-22
I am trying to help a family member configure the video settings.
So with only have ssh access, how do I figure out which NVIDIA (GeForce) card is in this system?

All I know is that the packaging says:
* It has an "NVIDIA ION" Chipset.
* Onboard Video is "NVIDIA ION graphics processor".

---

### Post by mikewhatever on 2011-01-22
You could run **lspci** or **lspci -v** for more info.

---

### Post by boondocks on 2011-01-22
Thanks, I did "lspci -vvvv" and then searched for the ION section...
```
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
        Subsystem: ZOTAC International (MCO) Ltd. Device a113
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at f8000000 (64-bit, prefetchable) [size=32M]
        Region 5: I/O ports at ec00 [size=128]
        [virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Kernel driver in use: nvidia
        Kernel modules: nvidia-current, nvidiafb, nouveau
```Yes, there is the nvidia Kernel driver. But I am still not sure - Which NVIDIA card is this?

---

### Post by cascade9 on 2011-01-22
Not really a 'card' exactly (its intergrated). Ion is ion. Its a different product line to the geforce or quadro cards.

---

### Post by endotherm on 2011-01-22
ion's are usually paired with low power architectures like Atom CPUs, so they are common in higher end netbooks. never used one with ubuntu, but my win7 netbook plays most older games very nicely.  overall i like it, but it does take a good bit more power than the intel gma.

---

### Post by boondocks on 2011-01-22
> **cascade9 said:**
> Not really a 'card' exactly (its intergrated)...
Correct. The word "card" was a poor choice.
I realize that - that is why I mentiond ... **Onboard Video** is "NVIDIA ION graphics processor"
When I came across "NVIDIA ION" Chipset, I started wondering.

> **cascade9 said:**
> ... Ion is ion. Its a different product line to the geforce or quadro cards.
Got it, thanks.
This is what I did not know.

---


---
title: "Pinnacle Dual Hybrid Pro PCI-E ( Saa7162 ) - Doesn't work with GUTSY GIBBON,pls help!"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by fcappy on 2007-10-19
Hi all, this is my first message on this community: here is my problem...

I bought that bulk card...but I cannot configure that under ubuntu Gutsy gubbon...anyone has any solution?
Here lspci returning code...

Output of 'lspci -vvxxx':

02:00.0 Multimedia controller: Philips Semiconductors Unknown device 7162
        Subsystem: Pinnacle Systems Inc. Unknown device 0100
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f7e00000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: [40] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [50] Express Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <256ns, L1 <1us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
                Link: Latency L0s <4us, L1 <64us
                Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [74] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [80] Vendor Specific Information
00: 31 11 62 71 07 01 10 00 00 00 80 04 10 00 00 00
10: 04 00 e0 f7 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 bd 11 00 01
30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 01 00 00
40: 05 50 8a 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 10 74 01 00 80 00 00 00 10 00 0a 00 11 6c 03 01
60: 08 00 11 00 00 0a 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 01 80 02 3e 00 00 00 00 00 00 00 00
80: 09 00 50 00 03 0c 00 00 02 02 00 00 00 00 00 00
90: 00 02 00 00 00 00 00 08 00 00 10 00 00 00 00 00
a0: 01 00 00 04 03 09 00 00 00 00 01 02 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 20 01 60 00 6b
c0: 01 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00



Unknown philips device 7162...:(

PLEASE HELP, I'm going mad...:mad::mad::mad:

---

### Post by fcappy on 2007-10-22
please, anyone who can help me...I cannot use this tv-card

---

### Post by Onurzaim on 2007-10-22
I have the PCI version of this card. It works fine under standard pal broadcasts but I cant watch DVB-T channels without firstly booting windows.

Good luck with your PCI-E card.

---

### Post by samborambo on 2007-10-22
This driver is still in development (for the PCIe DVB cards).

There's a kernel developer named "Manu" whose working on an open source driver under an NDA with NXP. Do some googling and you may be able to help him with driver testing. I think he's working on the QuattroS card last time I saw.

Sam.

---

### Post by fcappy on 2007-10-23
thank you dudes...for any update please post here!
I will do so...:popcorn:

---

### Post by fcappy on 2008-01-05
> **fcappy said:**
> thank you dudes...for any update please post here!
I will do so...:popcorn:

any updates?

---

### Post by fcappy on 2008-02-22
any update?

---


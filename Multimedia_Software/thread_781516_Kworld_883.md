---
title: "Kworld 883"
date: 2008-05-04
forum: Multimedia Software
---

### Post by dig314 on 2008-05-04
Kworld LTV883R Xpert TV DVD Maker PCI + TV Tuner Retail

This is a cheap card! Some posts claim it can work in Ubuntu.

Can someone tell me the Terminal commands to see if the hardware is being recognized correctly and the commands to try and configure it?

Thank you for your assistance.

Dig314

 lspci -vv # At least recognizes the chip

00:0f.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 165 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>



It is listed here:
[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/) (warning, HUGE page)
as 
issue date: 2004/3/25
pcb: KW88A_LP Ver:C
tuner: NTSC
connectors: FM,TV, AV-out (8pin fanout: cvid.,audio-L, audio-R, line out), remote
chip: cx23883-19
Here's the lspci -vv for it: PER [http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)
01:06.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+

---

### Post by dig314 on 2008-05-07
I have tried:

modprobe cx88xx card=16 tuner=2
modprobe cx8800

----
lspci -vv  still shows the same as above.


What else should I try ?

Dig314

---


---
title: "Troubles with mic on HP DV6000"
date: 2009-03-16
forum: Multimedia Software
---

### Post by tomlobato on 2009-03-16
I have a HP Pavilion DV6748. The audio output works fine, but mic nevers worked with Inptrepid. With Hardy Heron, I got it working by compiling kernel 2.6.23, but could not compile it on Inptrepid.

I tried several workarounds from [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") and other sources but with no success.

I`d like to know 2 things:
- Is there some advances regarding the above link method
- Could my mic work on Ubuntu 9.04 ?

If anything comes to rescue to make work my built-in mic, can you give opnions about using a USB sound adpater, like the attached image?


**# lspci |grep -i audio**
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

**# lspci -v**
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Hewlett-Packard Company Device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at f2580000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

**# lspci -vv**
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Device 30cf
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f2580000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
		Masking: 00000000  Pending: 00000000
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by tim183 on 2009-03-16
The same problem was reported here:
[http://ubuntuforums.org/showthread.php?t=1039685&highlight=hp+dv6000](http://ubuntuforums.org/showthread.php?t=1039685&highlight=hp+dv6000)

---


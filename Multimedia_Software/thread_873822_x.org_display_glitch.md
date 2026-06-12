---
title: "x.org display glitch"
date: 2008-07-29
forum: Multimedia Software
---

### Post by redbeardmcg on 2008-07-29
I have an issue with an NVIDIA quadro running nvidia sources. After a few minutes of using the system screen information starts to get overwritten. For example, if I scroll down a web page text and images start to disappear and over-write other portions of text. I can fix this by using pg up or pg down or clicking the titlebar. This happens in all applications except for gnome-terminal.

I am running the NVIDIA-Linux-x86-169.12 version of the NVIDIA driver as the nvidia module that shipped with the distro would not accept the X.org configuration necessary for my setup. I have posted lspci for this card below. There is nothing in the Xorg log or any other log.

cat /proc/version
Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008

sudo lspci -vvs 01:00.0
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 01f9
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at df00 [size=128]
	[virtual] Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <512ns, L1 <4us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM L0s L1 Enabled RCB 128 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x16

---


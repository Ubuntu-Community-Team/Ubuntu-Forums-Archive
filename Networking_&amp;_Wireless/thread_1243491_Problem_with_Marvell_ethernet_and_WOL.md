---
title: "Problem with Marvell ethernet and WOL"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by kolage on 2009-08-18
Hi,

I am using Arch linux and have problem with my

```

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)

```

which I am trying to use to WOL. I've read many forums, set

```

ethtool -s eth0 wol g

```

after starting and before every shutdown of computer, but it doesn't work, after soft power-off the led signals don't blink at all, but when I shutdown from Windows, it works. So now I am trying to set my network card before shutdown to some state that let it after shutdown alive. I tried to look on this:

```

# lspci -s 02:00.0 -vv
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Biostar Microtech Int'l Corp Device 2700
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 29
	Region 0: Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
	Region 2: I/O ports at bc00 [size=256]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
		Product Name: Marvell Yukon 88E8056 Gigabit Ethernet Controller
		Read-only fields:
			[PN] Part number: Yukon 88E8056
			[EC] Engineering changes: Rev. 1.3
			[MN] Manufacture ID: 4d 61 72 76 65 6c 6c
			[SN] Serial number: AbCdEfG749788
			[CP] Extended capability: 01 10 cc 03
			[RV] Reserved: checksum good, 9 byte(s) reserved
		Read/write fields:
			[RW] Read-write area: 121 byte(s) free
		End
	Capabilities: [5c] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 4181
	Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #3, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 unlimited
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 1f, GenCap- CGenEn- ChkCap- ChkEn-
	Kernel driver in use: sky2
	Kernel modules: sky2


```

and there one guy from Czech told me to change D status in [48] Power management capabilities. I try it with setpci, but don't know how to do that. Can anyone help me, please?

---

### Post by kolage on 2009-08-19
any advice, please? :confused:

---


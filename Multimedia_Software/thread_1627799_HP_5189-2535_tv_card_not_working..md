---
title: "HP 5189-2535 tv card not working."
date: 2010-11-21
forum: Multimedia Software
---

### Post by kmwatts on 2010-11-21
Has anyone gotten this tv card to work? I am having one heck of time trying to do so. Any help is greatly appreciated.
Ken

HP 5189-2535 ATSC/NTSC/QAM PCI Express (PCIe) Low Profile HDTV Tuner Card

# LG LGDT3304 VSB/QAM receiver chip
# Conexant CX23887-14Z PCIe A/V chip
# Conexant CX23417-11Z MEPG II A/V encoder chip
# PCI Express x1 interface

---

### Post by kmwatts on 2010-11-24
okay I give up, Anyone recommend a tv card that works with maverick?

---

### Post by xc3RnbFO8P on 2010-11-24
Can you show the output of:
> lspci -vn
and 
> dmesg

---

### Post by kmwatts on 2010-11-25
04:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 0f)
	Subsystem: Avermedia Technologies Inc Device de39
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at fde00000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data
		No end tag found
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 4199
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		AERCap:	First Error Pointer: 14, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [200 v1] Virtual Channel
		Caps:	LPEVC=1 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32+ WRR64+ WRR128-
		Ctrl:	ArbSelect=WRR64
		Status:	InProgress-
		Port Arbitration Table [240] <?>
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=1 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Kernel driver in use: cx23885
	Kernel modules: cx23885



[   10.594257] Linux video capture interface: v2.00
[   10.621415] cx23885 driver version 0.0.2 loaded
[   10.622106] IR NEC protocol handler initialized
[   10.625891] IR RC5(x) protocol handler initialized
[   10.627764] IR RC6 protocol handler initialized
[   10.627840] cx23885 0000:04:00.0: PCI INT A -> Link[LN4A] -> GSI 17 (level, low) -> IRQ 17
[   10.628019] CORE cx23885[0]: subsystem: 1461:de39, board: DViCO FusionHDTV5 Express [card=4,insmod option]
[   10.636601] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   10.732536] IR JVC protocol handler initialized
[   10.761821] cx23885_dvb_register() allocating 1 frontend(s)
[   10.761823] cx23885[0]: cx23885 based dvb card
[   10.765304] tuner-simple 1-0061: creating new instance
[   10.765306] tuner-simple 1-0061: type set to 64 (LG TDVS-H06xF)
[   10.765308] DVB: registering new adapter (cx23885[0])
[   10.765311] DVB: registering adapter 0 frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   10.765503] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   10.765508] cx23885[0]/0: found at 0000:04:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xfde00000
[   10.765514] cx23885 0000:04:00.0: setting latency timer to 64
[   10.765562]   alloc irq_desc for 44 on node 0
[   10.765563]   alloc kstat_irqs on node 0
[   10.765575] cx23885 0000:04:00.0: irq 44 for MSI/MSI-X

---

### Post by xc3RnbFO8P on 2010-11-26
Read this (and verify if its the same card):
[http://www.linuxtv.org/wiki/index.php/AVerMedia_M792_PCIe_Combo_(OEM)]("http://www.linuxtv.org/wiki/index.php/AVerMedia_M792_PCIe_Combo_(OEM)")

---

### Post by kmwatts on 2010-12-17
> **Ringi said:**
> Read this (and verify if its the same card):
[http://www.linuxtv.org/wiki/index.php/AVerMedia_M792_PCIe_Combo_(OEM)]("http://www.linuxtv.org/wiki/index.php/AVerMedia_M792_PCIe_Combo_(OEM)")
I believe it is the HP oem equivilent yes.
The cx23885 is supported and also the lgdt3304 is also. I think it could be made to work with the right tweaking.

---

### Post by kmwatts on 2010-12-21
bump

---


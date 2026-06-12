---
title: "Unable to acheive full dual band wireless speeds"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by JB-HIFI on 2012-04-20
Hi there. 

I've recently upgraded to a cisco e3000 router and while using windows 7 my wireless nic can associate to the access point at 300mbps, but using the broadcom sta driver in ubuntu 12.04 I can only seem to associate at 144mbps according to iwconfig anyway. I Don't want to sound like spoilt brat but I really want my 300mbps ! Any help would be appreciated. 

Thanks, Jonno.

Below is some information that could provide some help.


iwconfig

wlan0     IEEE 802.11abgn  ESSID:"Cisco29736"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: C0:C1:C0:EB:36:8B   
          Bit Rate=144.4 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0


lspci -vv

03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
	Subsystem: Dell Wireless 1520 Half-size Mini PCIe Card
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at b5800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [d0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
			ClockPM+ Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr+ BadTLP+ BadDLLP+ Rollover- Timeout+ NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-00-38-ff-ff-77-c0-cb
	Capabilities: [16c v1] Power Budgeting <?>
	Kernel driver in use: brcmsmac
	Kernel modules: wl, bcma, brcmsmac

---

### Post by newbie-user on 2012-04-21
Keep in mind that 300Mbps is a theoretical throughput and not a guaranteed number. With that said, Win7 might be yanking your chain when it says it's connecting at 300Mbps. The transfer rate varies greatly depending on location, settings, environment, etc. The only way to really test what speed you're getting is to actually transfer a file.

---

### Post by JB-HIFI on 2012-04-21
Hi. Thanks for the reply. I forgot to mention that I already tested transfer rates and can confirm that ubuntu operates at roughly half the speed.

I would really like the extra bandwidth as I move a lot of RAW files around.

I'm assuming it is some sort of driver issue. But I haven't been able to find anyone else having the same issue.

---


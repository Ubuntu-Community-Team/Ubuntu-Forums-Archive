---
title: "r8169 gone after apt-get upgrade"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by wiz561 on 2013-03-19
Hi!

I have had this reoccurring problem that whenever an update is applied to the system, eth0 disappears and I loose networking.  I then have to restart the box or restart networking, which brings eth0 back up.  I noticed that this-morning, eth0 was gone after this was automatically applied....

```
Start-Date: 2013-03-19  06:31:55
Install: linux-headers-3.2.0-39-generic:amd64 (3.2.0-39.62, automatic), linux-headers-3.2.0-39:amd64 (3.2.0-39.62, automatic), linux-image-3.2.0-39-generic:amd64 (3.2.0-39.62, automatic)
Upgrade: linux-server:amd64 (3.2.0.38.46, 3.2.0.39.47), apache2-mpm-prefork:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.3), apache2-utils:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.3), linux-headers-server:amd64 (3.2.0.38.46, 3.2.0.39.47), apache2:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.3), apache2.2-common:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.3), apache2.2-bin:amd64 (2.2.22-1ubuntu1.2, 2.2.22-1ubuntu1.3), linux-image-server:amd64 (3.2.0.38.46, 3.2.0.39.47), linux-libc-dev:amd64 (3.2.0-38.61, 3.2.0-39.62)
End-Date: 2013-03-19  06:33:21
```

It seems like it's always a 'linux-image' update that always breaks the networking.  I'm running Ubuntu 12.04 LTS server (no gui), and not using networking manager (as far as I can tell).

Here's my lspci info...

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 41
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at fdff8000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000aee0200d  Data: 4169
	Capabilities: [70] Express (v2) Endpoint, MSI 01
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
		Vector table: BAR=4 offset=00000000
		PBA: BAR=4 offset=00000800
	Capabilities: [d0] Vital Product Data
		No end tag found
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr+ BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169
```

The other thing I'm running on the machine that is kind of goofy is busybox before boot.  I have encrypted partitions and unlock LUKS by ssh'ing into the machine on a different IP and port and running an unlock script.  After the partition is unlocked, the old IP is disabled and linux boots up normally.

Thanks in advanced for any help because I'm at a loss here!

---


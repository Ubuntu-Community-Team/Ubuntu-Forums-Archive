---
title: "Wireless woes...!! :("
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by debayande on 2012-11-12
Hello.

I'm unable to connect to the wireless network at my home using my notebook (a Samsung R418.) I'm facing this problem on both Ubuntu and Xubuntu 12.10 (I use the 64-bit versions.) The same notebook, however, connects to the network mentioned above on Windows 7 Professional without any problems. Again, Ubuntu and its siblings are able to connect to wireless networks other than the one mentioned above on the same notebook without any problems.

The wireless router in question is a Cisco Linksys E1500, running DD-WRT v24-sp2 (06/08/12) big. The other machines on the network include a MacBook Pro running OS X Mountain Lion, an HTC One V running Android Ice Cream Sandwich, and a Nokia Lumia 610 running Windows Phone 7.5. These three devices can connect to the wireless network without any problems.

The network is secured using WPA2-Personal/AES. Whenever I try to connect, Ubuntu asks me for the pre-shared key. It then tries connecting to the network, fails, and drops me back to the key-entry dialog.

Here's what lspci has to say about my wireless card:

```

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```

And here's what dmesg has to say:

```

[   30.293868] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[ 1985.328259] Monitor-Mwait will be used to enter C-3 state
[ 2013.038522] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[ 2145.589758] wlan0: authenticate with xx:xx:xx:xx:xx
[ 2145.597314] wlan0: direct probe to xx:xx:xx:xx:xx (try 1/3)
[ 2145.800042] wlan0: direct probe to xx:xx:xx:xx:xx (try 2/3)
[ 2145.004041] wlan0: direct probe to xx:xx:xx:xx:xx (try 3/3)
[ 2145.208041] wlan0: authentication with xx:xx:xx:xx:xx timed out

```

*I've deliberately masked the MAC address in the code snippet above.*

Could someone kindly provide me some pointers on how to proceed? Thanks in advance.

---

### Post by ahallubuntu on 2012-11-12
Assuming this uses the ath9k driver: there is an option to disable hardware encryption with this driver that seems to fix some problems.  You might look it up and try that.

---

### Post by debayande on 2012-11-12
@ahallubuntu: I don't think it uses the ath9k driver. Here's why (check the last two lines of the code snippet below):

```

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Askey Computer Corp. Device 7131
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [90] MSI-X: Enable- Count=1 Masked-
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		AERCap:	First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [140 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

---

### Post by ahallubuntu on 2012-11-12
Yes, you're right - it uses the ath5k driver.

---


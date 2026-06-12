---
title: "Wake on Lan does not work with Ubuntu 12.04."
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by RubbelDieKatz on 2012-07-06
I have a Asus M4A77T board with RTL8111 gigabit Ethernet card. It is connected to a gigabit wlan router.

Acpi wake up event is set, the g flag on the card is set, network shutdown in /etc/init.d/halt is no.

So everything should be fine but I am not able to wake up the computer after shutdown from Ubuntu.

Until 12.04 WOL worked without any problem. If I shutdown Windows or other distros WOL works as expected.

**I have noticed the following difference**
The Router tells me that a Lan card is connected with 10Mbit only. If I use another OS it is set to 100Mbit after shutdown.

**So here are my questions.**[COLOR="Red"]
[LIST]Does anyone know how to force the card to stay connected with 100Mbit?[/LIST]
[LIST]
[*]Any other suggestions?
[/LIST][/COLOR]

_ethtool eth0_
```
Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
....
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes
```

_lspci -k_
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
	Kernel driver in use: r8169
	Kernel modules: r8169
```


_cat /proc/acpi/wakeup_
```
RLAN	  S4	*enabled   pci:0000:03:00.0
```

---

### Post by RubbelDieKatz on 2012-07-10
I still have no clue how to enable WOL in UBUNTU. 
But I have some more Informations.

If I suspend my computer there is the following line
```
r8169 0000:03:00.0: wake-up capability disabled by ACPI
```

Lspci -vv tells me that PME is disabled
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
....
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
.....

```

How can it be? PMA is enabled by the BIOS. RLAN wakeup is enabled 
in /proc/acpi/wakeup

Everyting seems to be fine. But the dammed DRIVER disables PME at the card.

Wow can I force the r8169 to enable PME?

---

### Post by The Linuxist on 2012-07-17
I don't think wake on LAN works for systems that are shutdown, only suspended.

---

### Post by markbl on 2012-07-17
> **The Linuxist said:**
> I don't think wake on LAN works for systems that are shutdown, only suspended.
You "don't think"? Of course WOL works for shutdown.

---

### Post by The Linuxist on 2012-07-18
Oh ok, well whenever I shutdown my PC, the link lights go off on the NIC and the switch port that the NIC is connected to, but when it's suspended they turn are on.

I really don't see how the NIC is going to get a magic packet when even the link layer isn't working.

---

### Post by markbl on 2012-07-18
> **The Linuxist said:**
> whenever I shutdown my PC, the link lights go off on the NIC and the switch port that the NIC is connected to, but when it's suspended they turn are on.
That's just because you have not set the option in your LAN card. You can do this with, e.g:
```

sudo ethtool -s eth0 wol g

```
You have to set this each time after a cold boot so just add this command at the end of /etc/rc.local (minus the sudo as it runs as root).
> 
I really don't see how the NIC is going to get a magic packet when even the link layer isn't working.
Because, so long as your network card and bios supports WOL, then the PC is powered up by them.

I use this all time. Just shut my PC down normally and, so long as I don't turn the power off at the wall any time, I can boot it up with a WOL magic packet, e.g. from my iphone. Suspend is buggy on my old PC so I never use it.

---

### Post by The Linuxist on 2012-07-18
Ah ok strange. I've got two computers here:
1) Dell Dimension E520
2) Asus something or other generic...

It works on the Dell, but not on the Asus. Sorry I feel like I've hijacked this thread now though.

---

### Post by The Linuxist on 2012-07-18
Ok, it does work on the ASUS as well, I'd just made a typo on /etc/rc.local

RubbelDieKatz, even though my card said that it has Wake-on: g enabled:

```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: yes
```it didn't work until I put the thing that markbl suggested into /etc/rc.local

Have you got that ethtool -s command in /etc/rc.local ?

---

### Post by markbl on 2012-07-18
Mine is an Asus and works ok ...

---

### Post by The Linuxist on 2012-07-18
> **markbl said:**
> Mine is an Asus and works ok ...

Thanks!

---

### Post by RubbelDieKatz on 2012-07-18
Meanwhile I found some threads about the problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/914439](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/914439)

The current r8169 kernel driver sucks. It does not shutdown the card correctly. Sometimes it even leaves the card in an incompatible state, so the cable-connection can not be detected.

There is a new driver r8168 that works much better with that card. 

[http://code.google.com/p/r8168/](http://code.google.com/p/r8168/)

The installation is very simple:
```
wget http://r8168.googlecode.com/files/r8168-8.031.00.tar.bz2
tar xjf r8168-8.031.00.tar.bz2
cd r8168-8.031.00
```
./autorun.sh

I had to reload the module after running autorun.
But it seems to work like a charme^

lspci -vv
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at f6fff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f6ff8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fbef0000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 41c1
	Capabilities: [70] Express (v2) Endpoint, MSI 01
		DevCap:	MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
	Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
		Vector table: BAR=4 offset=00000000
		PBA: BAR=4 offset=00000800
	Capabilities: [cc] Vital Product Data
		No end tag found
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
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
	Kernel driver in use: r8168
	Kernel modules: r8168

```

---


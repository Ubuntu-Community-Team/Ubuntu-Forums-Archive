---
title: "Broken Wireless Authentication"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by hicksid on 2011-08-09
diag o/p:


lspci -nn | grep 0280:

01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

lsmod | grep ath

ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath

sudo cat /var/log/syslog | grep etwork | tail -n10

Aug  9 19:20:32 hazel NetworkManager[428]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  9 19:26:47 hazel NetworkManager[428]: <info> (wlan0): DHCPv4 state changed bound -> renew
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   address 10.55.88.114
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   prefix 29 (255.255.255.248)
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   gateway 10.55.88.113
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   hostname 'hazel'
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   nameserver '192.168.22.22'
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   nameserver '192.168.22.23'
Aug  9 19:26:47 hazel NetworkManager[428]: <info>   domain name 'home'
Aug  9 19:26:47 hazel nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

---

### Post by lkjoel on 2011-08-09
Could you also give me the output of these Terminal commands?
```
sudo /etc/init.d/networking restart
sudo ifconfig
sudo iwconfig
sudo nm-tool
sudo rfkill list all
sudo lspci -vvnn

```

---

### Post by hicksid on 2011-08-10
sudo /etc/init.d/networking restart
[sudo] password for hazel: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:5d:fd:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:7d:3a:34  
          inet addr:10.55.88.115  Bcast:10.55.88.119  Mask:255.255.255.248
          inet6 addr: fe80::e60:76ff:fe7d:3a34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22901 (22.9 KB)  TX bytes:15868 (15.8 KB)

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTFON"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 0A:21:04:D6:3C:DA   
          Bit Rate=65 Mb/s   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        00:26:22:5D:FD:7D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto BTFON] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        0C:60:76:7D:3A:34

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTFON:           Infra, 02:24:17:F7:F1:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    BTOpenzone:      Infra, 02:24:17:E4:FB:A4, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    *BTFON:          Infra, 0A:21:04:D6:3C:DA, Freq 2452 MHz, Rate 54 Mb/s, Strength 95
    BTFON:           Infra, 02:26:44:1A:DD:F3, Freq 2457 MHz, Rate 54 Mb/s, Strength 42
    BTOpenzone:      Infra, 02:26:44:1A:DD:F2, Freq 2457 MHz, Rate 54 Mb/s, Strength 41
    BTHomeHub2-94FW: Infra, 00:26:44:1A:DD:F1, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    gearbox:         Infra, 00:21:04:D6:3C:DA, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTFON:           Infra, 02:24:2B:75:CF:4A, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
    BTOpenzone:      Infra, 02:24:2B:75:CF:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    BTOpenzone:      Infra, 06:21:04:D6:3C:DA, Freq 2452 MHz, Rate 54 Mb/s, Strength 100
    BTHomeHub2-94FW: Infra, 00:26:44:1A:DD:F1, Freq 2457 MHz, Rate 48 Mb/s, Strength 32 WEP
    Belkin_N_Wireless_4347e6: Infra, 94:44:52:43:47:E6, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Livebox-B140:    Infra, 00:19:7D:3C:72:F4, Freq 2457 MHz, Rate 54 Mb/s, Strength 34 WPA
    BTHomeHub2-53PG: Infra, 00:24:2B:75:CF:48, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2

  IPv4 Settings:
    Address:         10.55.88.115
    Prefix:          29 (255.255.255.248)
    Gateway:         10.55.88.113

    DNS:             62.6.40.178
    DNS:             62.6.40.162

sudo rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
sudo lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 58280000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at 60f0 [size=8]
	Region 2: Memory at 40000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at 58300000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: i915
	Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at 58200000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 46
	Region 0: Memory at 58340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 4189
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=0 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Capabilities: [130 v1] Root Complex Link
		Desc:	PortNumber=0f ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c000
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 57100000-581fffff
	Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #0, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4159
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=0 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=01 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 56100000-570fffff
	Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #1, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4161
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=0 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=02 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00003fff
	Memory behind bridge: 55000000-560fffff
	Prefetchable memory behind bridge: 0000000052000000-0000000052ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #3, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #2, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet+ LinkState+
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4169
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=0 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=03 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 54000000-54ffffff
	Prefetchable memory behind bridge: 0000000053000000-0000000053ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #4, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
			Slot #0, PowerLimit 6.500W; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4171
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100 v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=0 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Capabilities: [180 v1] Root Complex Link
		Desc:	PortNumber=04 ComponentID=02 EltType=Config
		Link0:	Desc:	TargetPort=00 TargetComponent=02 AssocRCRB- LinkType=MemMapped LinkValid+
			Addr:	00000000fed1c001
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 60a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 4: I/O ports at 6080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 6060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 19
	Region 4: I/O ports at 6040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 58344400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device [1025:022f]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 44
	Region 0: I/O ports at 60d8 [size=8]
	Region 1: I/O ports at 60fc [size=4]
	Region 2: I/O ports at 60d0 [size=8]
	Region 3: I/O ports at 60f8 [size=4]
	Region 4: I/O ports at 6020 [size=16]
	Region 5: Memory at 58344000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
		Address: fee0300c  Data: 4179
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 11
	Region 4: I/O ports at 6000 [size=32]
	Kernel modules: i2c-i801

01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e016]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at 57100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		DevCap2: Completion Timeout: Not Supported, TimeoutDis+
		DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
		LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
			 Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
			 Compliance De-emphasis: -6dB
		LnkSta2: Current De-emphasis Level: -6dB
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
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=01
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number 00-15-17-ff-ff-24-14-12
	Capabilities: [170 v1] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:022f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 45
	Region 0: Memory at 55000000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at 2000 [size=128]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0300c  Data: 4181
	Capabilities: [58] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [6c] Vital Product Data
pcilib: sysfs_read_vpd: read failed: Connection timed out
		Not readable
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP- SDES+ TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP+ Rollover- Timeout+ NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [180 v1] Device Serial Number ff-5d-fd-7d-00-26-22-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c

---

### Post by lkjoel on 2011-08-10
Could you give me the details of the problem?

---

### Post by hicksid on 2011-08-11
Hi, my problem is I am unable to connect to my local wireless network.
This operates with WPA/WPA2 encryption and works fine with my Windows7 laptop.
I can connect to unencrypted wireless networks with my ubuntu notebook but the DNS is broken so I am unable to do anything useful.
Thanks,
Ian

---

### Post by exchaoordo on 2011-08-11
I hope you don't mind me jumping in here but I'm having wireless troubles too with Ubuntu LTS 10.04 on  an Acer Aspire 532h that uses an Atherton wifi card.  My wifi will drop and not reacquire even though it sees the router.  Everything works in Windows and I've tried two different routers.  Problem is frustratingly intermittent. 
Here's my output from the commands you suggested.  I know only enough to get myself in trouble:
exchaoordo@acer-red:~$ sudo /etc/init.d/networking restart
[sudo] password for exchaoordo: 
 * Reconfiguring network interfaces...                                                                                [ OK ] 
exchaoordo@acer-red:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:28:45:ae  
          inet6 addr: fe80::725a:b6ff:fe28:45ae/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:62941935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2605 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:2549853 (2.5 MB)  TX bytes:401965 (401.9 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9584 (9.5 KB)  TX bytes:9584 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr c4:17:fe:9b:85:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20743770 (20.7 MB)  TX bytes:4695066 (4.6 MB)

exchaoordo@acer-red:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CustomCruiser"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by exchaoordo on 2011-08-11
Wait, there's more.  Is it possible this other router, Belkin is screwing things up for me?  I don't know what it is or how to tell the computer to ignore it.  Meanwhile, here's more output (done while connected via cable):
exchaoordo@acer-red:~$ sudo /etc/init.d/networking restart
[sudo] password for exchaoordo: 
 * Reconfiguring network interfaces...                                                                                [ OK ] 
exchaoordo@acer-red:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 70:5a:b6:28:45:ae  
          inet6 addr: fe80::725a:b6ff:fe28:45ae/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:62941935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2605 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:2549853 (2.5 MB)  TX bytes:401965 (401.9 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9584 (9.5 KB)  TX bytes:9584 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr c4:17:fe:9b:85:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20743770 (20.7 MB)  TX bytes:4695066 (4.6 MB)

exchaoordo@acer-red:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"CustomCruiser"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

AND:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

AND:

exchaoordo@acer-red:~$ sudo lspci -vvnn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 27
    Region 0: Memory at 98180000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at 60c0 [size=8]
    Region 2: Memory at 80000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at 98000000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0300c  Data: 4181
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at 98100000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 98200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 97000000-97ffffff
    Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
            Slot #  0, PowerLimit 6.500000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn+ PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0100c  Data: 4159
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 96000000-96ffffff
    Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
        LnkCap:    Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
            ClockPM- Suprise- LLActRep+ BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
            Slot #  1, PowerLimit 6.500000; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn+ PwrFlt- MRL- PresDet+ CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0100c  Data: 4161
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 4: I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 19
    Region 4: I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 98204400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device [1025:0349]

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 26
    Region 0: I/O ports at 60b8 [size=8]
    Region 1: I/O ports at 60cc [size=4]
    Region 2: I/O ports at 60b0 [size=8]
    Region 3: I/O ports at 60c8 [size=4]
    Region 4: I/O ports at 60a0 [size=16]
    Region 5: Memory at 98204000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0100c  Data: 4179
    Capabilities: [70] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 10
    Region 4: I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0349]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 28
    Region 0: Memory at 97000000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 5000 [size=128]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Address: 00000000fee0300c  Data: 4191
    Capabilities: [58] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [6c] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [180] Device Serial Number ff-b6-5a-70-ae-45-28-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e016]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at 96000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: 00000000  Data: 0000
    Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

exchaoordo@acer-red:~$

---

### Post by chili555 on 2011-08-16
> **hicksid said:**
> Hi, my problem is I am unable to connect to my local wireless network.
This operates with WPA/WPA2 encryption and works fine with my Windows7 laptop.
I can connect to unencrypted wireless networks with my ubuntu notebook but the DNS is broken so I am unable to do anything useful.
Thanks,
IanWhich network are you trying to connect to but are unable to? What I see here is a Network Manager (and chili555) nightmare:> Wireless Access Points (* = current AP)
BTFON: Infra, 02:24:17:F7:F1:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
BTOpenzone: Infra, 02:24:17:E4:FB:A4, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
*BTFON: Infra, 0A:21:04:D6:3C:DA, Freq 2452 MHz, Rate 54 Mb/s, Strength 95
BTFON: Infra, 02:26:44:1A:DD:F3, Freq 2457 MHz, Rate 54 Mb/s, Strength 42
BTOpenzone: Infra, 02:26:44:1A:DD:F2, Freq 2457 MHz, Rate 54 Mb/s, Strength 41
BTHomeHub2-94FW: Infra, 00:26:44:1A:DD:F1, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
gearbox: Infra, 00:21:04:D6:3C:DA, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
BTFON: Infra, 02:24:2B:75:CF:4A, Freq 2462 MHz, Rate 54 Mb/s, Strength 45
BTOpenzone: Infra, 02:24:2B:75:CF:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
BTOpenzone: Infra, 06:21:04:D6:3C:DA, Freq 2452 MHz, Rate 54 Mb/s, Strength 100
BTHomeHub2-94FW: Infra, 00:26:44:1A:DD:F1, Freq 2457 MHz, Rate 48 Mb/s, Strength 32 WEP
Belkin_N_Wireless_4347e6: Infra, 94:44:52:43:47:E6, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
Livebox-B140: Infra, 00:19:7D:3C:72:F4, Freq 2457 MHz, Rate 54 Mb/s, Strength 34 WPA
BTHomeHub2-53PG: Infra, 00:24:2B:75:CF:48, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
It's a nightmare because there are several access points with the same ESSID, BTFON for example, causing NM to roam from among them. On the computer's end, it is a constant series of disconnects and re-connects. I understand that it shouldn't be that way, but that is currently NMs behavior.

The other thing I see is access points with mixed mode WPA *and* WPA2 encryption; this is very difficult for some driver > wpa_supplicant > NM combinations to handle.

Just to satisfy my curiosity, are these access points owned and administered by the provider? British Telecom, per chance? 

You might try making your driver ath9k use software encryption instead of hardware:```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```If it helps, we can write a config file to make it persistent.

---

### Post by hicksid on 2011-08-16
Hi Chilli,
I'm trying to connect to my own network "gearbox" and yes, it is a BT provided DSL line.

Results of cmds:
sudo ifconfig wlan0 down - done
sudo rmmod -f ath9k - done
sudo modprobe ath9k nohwcrypt=1 - done
sudo ifconfig wlan0 up - done

Still no change, cannot connect to 'gearbox'. Only connects to 'BTFON' which is sort of OK but the DNS doesn't work so its not much use.

The router is set to use WPA && WPA2 so I cannot see how to make it use one or the other but not both - guess this is negotiated as part of the wireless handshaking protocol ?

---

### Post by chili555 on 2011-08-16
> I'm trying to connect to my own network "gearbox" By golly, now we're getting somewhere! If it is your own network, meaning a router you own or lease and administer, then I'd set the encryption to WPA2 *only* in the admin pages of the router. Please see attached.

---

### Post by hicksid on 2011-08-16
Hi, I am unable to select only one encryption scheme.

---

### Post by airper on 2011-08-16
[SIZE=2]Hi, hope you don't mind me joining this thread, 

I have exactly the same problem. BT Internet, with their supplied router and the Atheros AR9285 wilreless card, fitted to a Toshiba Satellite R830-145

Firstly the settings on the router to change to WPA2 are under - advanced, wireless, security. All the options are there and I have just successfully changed mine.

That alone did not solve the problem, so I then ran the commands given previously to change from hardware to software encryption.

I ran this, output below, but it created errors with the driver and has killed all the connections in Network Manager. wired, wireless were both disabled immediately after running the commands below.

Command outputs

                     [/SIZE]            [FONT=Liberation Sans, sans-serif][SIZE=2]sudo ifconfig wlan0 down [/SIZE][/FONT] 
[FONT=Liberation Sans, sans-serif][SIZE=2][sudo] password for wayne: [/SIZE][/FONT] 
[FONT=Liberation Sans, sans-serif][SIZE=2]wayne@wayne-SATELLITE-R830 ~ $ sudo rmmod -f ath9k [/SIZE][/FONT] 
[FONT=Liberation Sans, sans-serif][SIZE=2]wayne@wayne-SATELLITE-R830 ~ $ sudo modprobe ath9k nohcrypt=1 [/SIZE][/FONT] 
[FONT=Liberation Sans, sans-serif][SIZE=2]FATAL: Error inserting ath9k (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg) [/SIZE][/FONT] 
[FONT=Liberation Sans, sans-serif][SIZE=2]wayne@wayne-SATELLITE-R830 ~ $ sudo ifconfig wlan0 up [/SIZE][/FONT] 
[FONT=Liberation Sans, sans-serif][SIZE=2]wlan0: ERROR while getting interface flags: No such device[/SIZE][/FONT]
[SIZE=2]
[/SIZE]
[FONT=Liberation Sans, sans-serif][SIZE=2]I rebooted and they came back up, but I still can't connect via the router using Ubuntu 11.04 on this PC. For info the connection is okay via Windows 7 on this PC and also using Ubuntu on other computers. 

I can use a 3G dongle on this PC in Ubuntu okay, so that is working.

Can post more command output if that would be helpful.[/SIZE][/FONT]


[FONT=Liberation Sans, sans-serif][SIZE=2]Further info, I have exactly the same issue on an Acer 7551, the wireless card in this case is an Atheros AR928X
[/SIZE][/FONT]

---

### Post by chili555 on 2011-08-16
> sudo modprobe ath9k nohcrypt=1
FATAL: Error inserting ath9k (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg) The unknown parameter is because it's:```
sudo modprobe ath9k noh[COLOR="Red"]w[/COLOR]crypt=1
```Please try it and give us your report; we want this to succeed.> I can connect to unencrypted wireless networks with my ubuntu notebook but the DNS is broken so I am unable to do anything useful.Can we fix it so you can connect for now? While connected to the unencrypted network, please post:```
cat /etc/resolv.conf
```

---

### Post by hicksid on 2011-08-17
Hi Chilli,
I lied in my previous post - I am able to select just one encryption type, so I tried WPA on its own, then WEP on its own and then no authentication. Still not able to pick up'gearbox' which is now very odd as I was convinced it was an encryption problem.
 
Any ideas ?
 
TIA

---

### Post by airper on 2011-08-17
My apologies Chili for the typo, I corrected this and the commands ran fine, connections showing in Network Manager, but still the authentication does not complete.

I too cannot connect to unencrypted networks. I have reset my router to WPA only, WEP only and none, without success. I have also tried two public access points (BT openzone) no luck with these either.

I'm not sure if this is relevant to the issue, but I also can't connect this computer to the router via a wired connection. Essentially it appears to be the same condition. eth0 shows up in Network Manager, but appears to time out during the authentication process. It's fine on Win7 and other PCs running Ubuntu.

---

### Post by airper on 2011-08-17
Hi, I've done a little more research on the router this evening. Under the home network tab it lists the devices that are currently connected and devices that have been connected.

I have grabbed three screenshots to help I hope. In the list of connected_devices_now, two PC's, both running Ubuntu are connected, one wireless one ethernet.

In the list, connected_devices_list and  connected_devices_list2, you can see wayne_SATELLITE-R830 is reporting it has been connected via ethernet and wireless, however, authentication was never completed so these was never useable connections. (left hand column is ethernet, right hand column is wireless)

The router is definitely in WPA2 mode, but in network manager connection details, authentication is listed as WPA/WPA2, no entry seems to appear in the drop down matching the routers WPA2 only I don't know if this is significant.

I'm not sure what this actually means, but there would appear to be some communication at least between the laptop and the router.

---

### Post by airper on 2011-08-17
double post

---

### Post by chili555 on 2011-08-17
If you Google ath9k and Natty, the results are dismal. Unresolved bugs, complaints, proposed but unconfirmed fixes, etc., etc.

I'd like to concentrate on hicksid because he, she or it started the thread. The others can try the proposed fixes and, if necessary after hicksid is hopefully fixed, we can work on others one at a time. I have trouble working on three or four cases in the same thread and trying to keep everyone's specifics straight. My bad.

hicksid, please open a terminal and do:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Add a single line:```
options ath9k nohwcrypt=1
```Proofread carefully, save and close gedit. Reboot.

Do you see 'gearbox' when you click the Network Manager icon? When you click it, does it try to connect and fail? Are there any interesting clues here?```
sudo cat /var/log/syslog | grep ath9k | tail -n25
```

I have on my horizon compat-wireless.

---

### Post by airper on 2011-08-18
No worries chili, I can entirely understand that approach.

I'll hang on in there at the back following along, but being quiet. I have a feeling that once this is resolved for one person, the solution will sort out most other people too, hope so anyway.

Learning a lot in the process too, which is all to the good.

Best Regards

---

### Post by hicksid on 2011-08-18
OK Chilli, done the ath9k.conf mod as requested and rebooted. Here is o/p from syslog:

Aug 16 19:57:26 hazel NetworkManager[432]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 4)
Aug 18 19:13:51 hazel kernel: [   16.553361] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 18 19:13:51 hazel kernel: [   16.553391] ath9k 0000:01:00.0: setting latency timer to 64
Aug 18 19:13:51 hazel kernel: [   16.652423] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 18 19:13:51 hazel kernel: [   16.655283] Registered led device: ath9k-phy0::radio
Aug 18 19:13:51 hazel kernel: [   16.655493] Registered led device: ath9k-phy0::assoc
Aug 18 19:13:51 hazel kernel: [   16.655679] Registered led device: ath9k-phy0::tx
Aug 18 19:13:51 hazel kernel: [   16.655927] Registered led device: ath9k-phy0::rx
Aug 18 19:13:51 hazel NetworkManager[431]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Aug 18 19:31:07 hazel kernel: [   13.123863] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 18 19:31:07 hazel kernel: [   13.123890] ath9k 0000:01:00.0: setting latency timer to 64
Aug 18 19:31:07 hazel kernel: [   13.693635] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 18 19:31:07 hazel kernel: [   13.695639] Registered led device: ath9k-phy0::radio
Aug 18 19:31:07 hazel kernel: [   13.695751] Registered led device: ath9k-phy0::assoc
Aug 18 19:31:07 hazel kernel: [   13.695844] Registered led device: ath9k-phy0::tx
Aug 18 19:31:07 hazel kernel: [   13.695940] Registered led device: ath9k-phy0::rx
Aug 18 19:31:13 hazel NetworkManager[690]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Aug 18 19:42:25 hazel kernel: [   17.536430] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 18 19:42:25 hazel kernel: [   17.536460] ath9k 0000:01:00.0: setting latency timer to 64
Aug 18 19:42:25 hazel kernel: [   17.658394] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Aug 18 19:42:25 hazel kernel: [   17.662202] Registered led device: ath9k-phy0::radio
Aug 18 19:42:25 hazel kernel: [   17.662422] Registered led device: ath9k-phy0::assoc
Aug 18 19:42:25 hazel kernel: [   17.662642] Registered led device: ath9k-phy0::tx
Aug 18 19:42:25 hazel kernel: [   17.662851] Registered led device: ath9k-phy0::rx
Aug 18 19:42:25 hazel NetworkManager[397]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)

---

### Post by hicksid on 2011-08-18
one other thing - when i connect wired to my router, everything works fine (DHCP, DNS, web-browsing)

---

### Post by chili555 on 2011-08-19
I have two suggestions. First, today I got an updated linux-image from Update Manager. If you are running Natty 11.04, you will, too. Please open Update Manager, press Check and let UM check for updates. Install them. Reboot and see if your wireless is working.

If not, let's install compat-wireless. Here are the instructions with the change that your driver-select will be *ath*. You can skip the modprobe step and reboot instead.

[http://ubuntuforums.org/showpost.php?p=11061867&postcount=6](http://ubuntuforums.org/showpost.php?p=11061867&postcount=6)

I downloaded it myself just now. It 'makes' with a very few warnings and no errors. I don't have the hardware, so I can't test it. Let us know how it goes.

---

### Post by hicksid on 2011-08-20
Thanks Chilli, I have downloaded and installed compat-wireless and also checked I have latest updates with UM.

Wireless connectivity has improved, I can now connect reliably to non-encrypted wireless access points (BTFON in the UK) but I can still not connect to my own router using wireless encryption.

Regards,
Ian

---

### Post by chili555 on 2011-08-20
Is the performance the same both with and without the /etc/modprobe.d/ath9k.conf file we wrote?

Sadly, reading the large number of complaints about ath9k, I'm convinced it is broken. In previous Ubuntu versions it was among the easiest and most reliable. The last suggestion I have is to download the live CD for Ubuntu 10.04 LTS and see if ath9k works reliably there. If so, after backing up /home, I'd install it and use it. I'm sorry. I wish I had a better answer.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by hicksid on 2011-08-20
Hi chili555,
No difference when I comment out the entry in ath9k.conf.
I tried running 10.04, but no change there either.
I'm no expert but it points to an encryption issue possibly ? - maybe a incompatability issue between how the laptop is encrypting the wireless connection and how the router is doing the same thing. What do you think ?
Regards,
Ian
PS many thanks for all your efforts so far.

---

### Post by chili555 on 2011-08-20
> it points to an encryption issue possibly ? It's hard to tell. Encryption in software is handled by wpa_supplicant, and in hardware, by the wireless chip itself. However you have tried both ways:> options ath9k nohwcrypt=1If you temporarily remove encryption from your router, does it connect now that you are using the compat-wireless driver?

Many thousands of us here have no issue whatever with encryption; i.e. wpa_supplicant. I think it's the ath9k driver or its interaction with wpa_supplicant and Network Manager.> Only connects to 'BTFON' which is sort of OK but the DNS doesn't work so its not much use.What is wrong with the DNS on BTFON? Why don't we use our own DNS nameservers?

---

### Post by hicksid on 2011-08-22
Is there any mileage in manually configuring a config file with the necessary parameters ? Would you know what to configure ? Is there any diagnostics info for wpa_supplicant ?

---

### Post by hicksid on 2011-08-22
chili555,

I notice I dont have a wpa_supplicant.conf file. Is this bad ?

---

### Post by chili555 on 2011-08-22
> Is there any mileage in manually configuring a config file with the necessary parameters ? Would you know what to configure ? Is there any diagnostics info for wpa_supplicant ?I do know what files to configure. There are at least two ways to do it. The easiest is /etc/network/interfaces. Here is a sample:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-essid gearbox
wpa-psk yourkey
```Or you could try:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.112
netmask 255.255.255.0
gateway 192.168.1.1
wpa-essid gearbox
wpa-psk yourkey
```There is an alternative method involving wpa_supplicant.conf. It's a bit more complex, but doesn't do much for you that the above doesn't do.

Neither method will work alongside Network Manager. It must be, as it is on the computer I'm responding on at this moment, removed completely. The only thing manual methods will do for us is rule out NM as the non-working or conflicting piece of the puzzle.

You could also try Wicd.

I will be happy to assist you in any way you want to try. I am convinced that ath9k is the defective part. That we could bypass with ndiswrapper. Tell me how you'd like to proceed and I'll be happy to assist.

---

### Post by praseodym on 2011-08-22
Open the file via

```
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
Add the following:

```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
# 0: The driver of the interface is responsible for scanning and choses the access point.
#    This mode should be used if a wired connection should be encrypted, too.
# 1: wpa_supplicant is responsible for scanning and choses the access point.
# 2: Nearly like "0", but connects with security policies and (E)SSID to AP (BSSID not supported)
#
# Normally mode "0" or "1" works.

ap_scan=1
```
plus encryption entries for WPA _and_ WPA2, respectively. Examples for possible encryption modes [here]("http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA2-Verschluesselung") (Wiki in German, but should be self-explaining). The entries for "group" and "pairwise" are listed _for your corresponding_ Network by

```
sudo iwlist scan
```

---

### Post by chili555 on 2011-08-22
>  /etc/wpa_supplicant/wpa_supplicant.confWhat process calls the file if it didn't exist previously but now does? Network Manager? Or...what?

---

### Post by praseodym on 2011-08-22
The package **wpasupplicant** normally is installed by default. You can start the debug-mode via:

```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d 
```

if the wpa_supplicant.conf exists. If the output repeats constantly, it can be stopped by CTRL+C.

---

### Post by hicksid on 2011-08-23
OK thanks for the info. One question:
 
How do I remove NM completely ?
 
Thanks.

---

### Post by hicksid on 2011-08-23
Hi,
[SIZE=2]This file doesn't exist on my system.[/SIZE]
 
> **praseodym said:**
> Open the file via
 
```
gksudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
Add the following:
 
 
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
# 0: The driver of the interface is responsible for scanning and choses the access point.
#    This mode should be used if a wired connection should be encrypted, too.
# 1: wpa_supplicant is responsible for scanning and choses the access point.
# 2: Nearly like "0", but connects with security policies and (E)SSID to AP (BSSID not supported)
#
# Normally mode "0" or "1" works.
 
ap_scan=1
```
plus encryption entries for WPA _and_ WPA2, respectively. Examples for possible encryption modes [here]("http://wiki.ubuntuusers.de/WLAN/wpa_supplicant#WPA2-Verschluesselung") (Wiki in German, but should be self-explaining). The entries for "group" and "pairwise" are listed _for your corresponding_ Network by
 
```
sudo iwlist scan
```

---

### Post by praseodym on 2011-08-23
It doesnt exist on my system either, you have to create it. Show

```
sudo iwlist scan
```
and name your network you want to connect to. Is the package **wpasuplicant** installed?

---

### Post by hicksid on 2011-08-23
> **praseodym said:**
> It doesnt exist on my system either, you have to create it. Show

```
sudo iwlist scan
```
and name your network you want to connect to. Is the package **wpasuplicant** installed?

OK, switched off NM using:

sudo update-rc.d NetworkManager remove

and also sudo service network-manager stop

sudo iwlist scan o/p:

Cell 03 - Address: 00:21:04:D6:3C:DA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"gearbox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bdaa118d0
                    Extra: Last beacon: 384ms ago
                    IE: Unknown: 000767656172626F78
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000

wpa_supplicant.conf:


ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
network={
	ssid="gearbox"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=TKIP
	psk="<my key was here>"
}


Debug output:

/etc/wpa_supplicant$ sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant/wpa_supplicant.conf -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=1
Priority group 0
   id=0 ssid='gearbox'
WEXT: cfg80211-based driver detected
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
netlink: Operstate: linkmode=1, operstate=5
Own MAC address: 0c:60:76:7d:3a:34
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 36 39 db 70 71 d6 53 2e 9a c1 4d f6 80 56 cb 08
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: Supplicant port status: Unauthorized
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: Supplicant port status: Unauthorized
EAPOL: Supplicant port status: Unauthorized
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
State: DISCONNECTED -> SCANNING
Scan SSID - hexdump_ascii(len=7):
     67 65 61 72 62 6f 78                              gearbox         
Starting AP scan for specific SSID(s)
Scan requested (ret=0) - scan timeout 5 seconds
EAPOL: disable timer tick
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 2617 bytes of scan results (6 BSSes)
BSS: Start scan result update 1
BSS: Add new id 0 BSSID 00:21:04:d6:3c:da SSID 'gearbox'
BSS: Add new id 1 BSSID 00:26:44:1a:dd:f1 SSID 'BTHomeHub2-94FW'
BSS: Add new id 2 BSSID 06:21:04:d6:3c:da SSID 'BTOpenzone'
BSS: Add new id 3 BSSID 0a:21:04:d6:3c:da SSID 'BTFON'
BSS: Add new id 4 BSSID 02:26:44:1a:dd:f3 SSID 'BTFON'
BSS: Add new id 5 BSSID 02:26:44:1a:dd:f2 SSID 'BTOpenzone'
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:21:04:d6:3c:da ssid='gearbox' wpa_ie_len=26 rsn_ie_len=24 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:21:04:d6:3c:da ssid='gearbox'
Trying to associate with 00:21:04:d6:3c:da (SSID='gearbox' freq=2452 MHz)
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2 proto 2
WPA: set AP WPA IE - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 04 00 50 f2 02 01 00 00 50 f2 02
WPA: set AP RSN IE - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP fail=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portControl=Auto
EAPOL: Supplicant port status: Unauthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=15
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=125
AssocResp IE wireless event - hexdump(len=117): 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 8d 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 09 00 03 7f 01 01 00 00 ff 7f 2d 1a 4c 10 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 09 08 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 0a 00 03 7f 04 01 00 00 00 00 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:21:04:d6:3c:da
Association info event
resp_ies - hexdump(len=117): 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c dd 18 00 50 f2 02 01 01 8d 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00 dd 09 00 03 7f 01 01 00 00 ff 7f 2d 1a 4c 10 1b ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 09 08 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 0a 00 03 7f 04 01 00 00 00 00 00
FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
netlink: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:21:04:d6:3c:da
No keys have been configured - skip key clearing
Associated with 00:21:04:d6:3c:da
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portValid=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - EAP success=0
EAPOL: Supplicant port status: Unauthorized
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: enable timer tick
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:21:04:d6:3c:da
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=2
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 11 54 1a 56 ce f2 a5 ac 60 e7 dc a7 1e 6a 92 70 81 56 5b 04 67 d6 e4 a6 ca 8d c4 51 f8 b1 87 30
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:21:04:d6:3c:da (ver=2)
RSN: msg 1/4 key data - hexdump(len=0):
WPA: Renewed SNonce - hexdump(len=32): ad fe 30 1c af de c9 d2 85 71 55 87 7a 90 1f e2 39 d3 ad e1 4f 1b 47 99 3b b0 86 02 d4 28 d9 bb
WPA: PTK derivation - A1=0c:60:76:7d:3a:34 A2=00:21:04:d6:3c:da
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=48): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:21:04:d6:3c:da
IEEE 802.1X RX: version=1 type=3 length=175
  EAPOL-Key type=2
  key_info 0x13ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC Secure Encr)
  key_length=16 key_data_length=80
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 11 54 1a 56 ce f2 a5 ac 60 e7 dc a7 1e 6a 92 70 81 56 5b 04 67 d6 e4 a6 ca 8d c4 51 f8 b1 87 30
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 49 07 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): fd f2 09 2d c0 b9 90 a3 e3 b0 5a 1a 16 7a 1a 9c
RSN: encrypted key data - hexdump(len=80): 03 fe ee f2 d4 13 5d a3 e6 c1 68 6e 94 73 f3 db 8a 01 07 d9 5d 9e fa a9 46 65 be b4 e8 47 37 d8 76 a1 05 1b e8 8e e3 51 19 46 1a a3 d4 9c 11 fc 13 ce d2 a6 19 5f 80 c4 e8 81 af 41 28 93 57 5e e5 51 4f 3f 47 c2 ab e0 2b 1a d1 c4 5f 24 22 74
WPA: decrypted EAPOL-Key key data - hexdump(len=72): [REMOVED]
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:21:04:d6:3c:da (ver=2)
WPA: IE KeyData - hexdump(len=72): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00 dd 26 00 0f ac 01 02 00 1f 9d f7 5f 30 a2 86 6f 35 7b 4c a9 76 24 19 c5 89 cc a9 61 32 c8 76 c0 1d 38 3f a2 7a a0 dc f3 dd 00 00 00 00 00
WPA: RSN IE in EAPOL-Key - hexdump(len=26): 30 18 01 00 00 0f ac 02 02 00 00 0f ac 04 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: GTK in EAPOL-Key - hexdump(len=40): [REMOVED]
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
EAPOL: External notification - portValid=1
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RSN: received GTK in pairwise handshake - hexdump(len=34): [REMOVED]
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=2 tx=0 len=32).
WPA: RSC - hexdump(len=6): 49 07 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=2 set_tx=0 seq_len=6 key_len=32
WPA: Key negotiation completed with 00:21:04:d6:3c:da [PTK=CCMP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:21:04:d6:3c:da completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
netlink: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: Supplicant port status: Authorized
EAPOL: SUPP_BE entering state IDLE
EAPOL authentication completed successfully
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
EAPOL: startWhen --> 0
EAPOL: disable timer tick
RX EAPOL from 00:21:04:d6:3c:da
IEEE 802.1X RX: version=1 type=3 length=143
  EAPOL-Key type=2
  key_info 0x1382 (ver=2 keyidx=0 rsvd=0 Group Ack MIC Secure Encr)
  key_length=32 key_data_length=48
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 11 54 1a 56 ce f2 a5 ac 60 e7 dc a7 1e 6a 92 70 81 56 5b 04 67 d6 e4 a6 ca 8d c4 51 f8 b1 87 31
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 2d 65 69 c3 99 f1 87 cd d2 75 e8 82 2e 09 74 8d
RSN: encrypted key data - hexdump(len=48): 63 58 14 23 16 50 59 a2 34 7d 49 44 12 ee 8c a7 23 82 c1 fe 47 95 4c b4 e6 17 8f c3 37 84 68 d1 fc f9 b9 2b be db 22 d0 e4 5a e8 11 38 8b 47 2f
WPA: decrypted EAPOL-Key key data - hexdump(len=40): [REMOVED]
WPA: RX message 1 of Group Key Handshake from 00:21:04:d6:3c:da (ver=2)
RSN: msg 1/2 key data - hexdump(len=40): dd 26 00 0f ac 01 01 00 94 85 88 67 19 62 74 96 89 6d 8b 62 5d d4 59 51 85 58 9d 7e ed db 0b 66 fe f5 63 25 27 6e 38 57
WPA: GTK in EAPOL-Key - hexdump(len=40): [REMOVED]
RSN: received GTK in group key handshake - hexdump(len=34): 01 00 94 85 88 67 19 62 74 96 89 6d 8b 62 5d d4 59 51 85 58 9d 7e ed db 0b 66 fe f5 63 25 27 6e 38 57
State: COMPLETED -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0 len=32).
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: Group rekeying completed with 00:21:04:d6:3c:da [GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED

---

### Post by praseodym on 2011-08-23
You are using mixed WPA/WPA2 encrytion, so you have to add another pair of data to the file for WPA as you did for WPA2, just add it below. If CCMP and TKIP are used, CCMP should be preferred at "pairwise".

You should transfer the ASCII key into hex and put it into the file without "". If you want to create a secure key:

```
sudo apt-get install pwgen
pwgen -c -n -s 63 1           #create a 63-log-key
wpa_passphrase gearbox yourkeyyouwanttouse
```
This key should be copied into the file. Dont forget to change the key (if you want to change it) in your router, too.

---

### Post by hicksid on 2011-08-23
> **praseodym said:**
> You are using mixed WPA/WPA2 encrytion, so you have to add another pair of data to the file for WPA as you did for WPA2, just add it below. If CCMP and TKIP are used, CCMP should be preferred at "pairwise".

You should transfer the ASCII key into hex and put it into the file without "". If you want to create a secure key:

```
sudo apt-get install pwgen
pwgen -c -n -s 63 1           #create a 63-log-key
wpa_passphrase gearbox yourkeyyouwanttouse
```
This key should be copied into the file. Dont forget to change the key (if you want to change it) in your router, too.

Sorry, I'm getting confused. Should I be editing the wpa_supplicant.conf file ? If I remove the quotes from around my psk parameter, I get a parsing error.

---

### Post by praseodym on 2011-08-23
If you remove the quotes the key has to be hexadecimal, not ASCII.

Yes, you should add the following WPA-config to the wpa_supplicant.conf below the WPA2-config, otherwise WPA is not configured:

```
network={
ssid="gearbox"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=CCMP # CCMP should be preferred, at the WPA2-config, too
group=TKIP
psk="<my key was here>"
}
```

---

### Post by hicksid on 2011-08-24
OK, thanks. I've done that now.

I see a new interface:

wlan0:avahi

but it has not been assigned an IP address by DHCP (its address is 169.254.5.176 which is I believe a reserved address)

---

### Post by hicksid on 2011-08-24
also, when I do a iwconfig, the wlan0 interface shows increasing pkt count against "Invalid misc"

---

### Post by praseodym on 2011-08-25
Can you try:
```
sudo ifdown wlan0
sudo ifup wlan0
sudo dhclient wlan0
```
and show:

```
ifconfig -a
iwconfig
sudo iwlist wlan0 scan
iwlist wlan0 chan
route -n
```

---

### Post by hicksid on 2011-08-25
sudo ifdown wlan0:

my wireless LED does go out

sudo ifup wlan0:

wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/networks/if-pre-up.d/wpasupplicant exoted with return code 1

my wireless LED does light up though.

sudo dhclient wlan0:

no output and hangs so I have to ctrl-C

Output from show:

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:22:5d:fd:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5680 (5.6 KB)  TX bytes:5680 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:7d:3a:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25874 (25.8 KB)  TX bytes:15236 (15.2 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"gearbox"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:21:04:D6:3C:DA   
          Bit Rate=65 Mb/s   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0
sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:04:D6:3C:DA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"gearbox"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044c79126a3
                    Extra: Last beacon: 388ms ago
                    IE: Unknown: 000767656172626F78
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 02 - Address: 06:21:04:D6:3C:DA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044c78ff180
                    Extra: Last beacon: 416ms ago
                    IE: Unknown: 000A42544F70656E7A6F6E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 0A:21:04:D6:3C:DA
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000044c78ff180
                    Extra: Last beacon: 440ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018D0003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010020FF7F
                    IE: Unknown: DD0A00037F04010000000000

iwlist wlan0 chan
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.452 GHz (Channel 9)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
hazel@hazel:/etc/network$

---

### Post by praseodym on 2011-08-25
Shut down the Power Management:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
You may set up a new wireless profile in the NM applet.

---

### Post by hicksid on 2011-08-26
thanks but I dont follow your logic and it hasn't helped anyway as I dont still get an IP address from my router.

---

### Post by airper on 2011-08-28
Hi Hicksid,

I was following along with your thread, then chili responded to one of my threads on the Mint Forum. With super help from chili, I tried the latest ath9k drivers, compat-wireless and ndiswrapper. 

None of these have worked for me, but they might give you a clue, given you are using  different laptop. The thread is here if it helps.

[http://forums.linuxmint.com/viewtopic.php?f=53&t=79969](http://forums.linuxmint.com/viewtopic.php?f=53&t=79969)

Given we can't get the on-board card working, Chili has suggested trying a usb wifi dongle details here for that.

[https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04](https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04)

It is available on Amazon UK as well. I've ordered one to try it, can let you know how it get on with it, if that is helpful to you.

Regards

Wayne

---

### Post by hicksid on 2011-08-29
Thanks Wayne, I appreciate the additional info and the helpful comments.
Its an idea to use a wireless dongle but I really want to avoid it if possible. Its a frustrating issue given that it works under windows and android but not ubuntu which I like as an OS.
All the best,
Ian

---

### Post by airper on 2011-08-29
Yep, agree, this laptop is fine in windows, connects to everything no problem. However, I much prefer Linux, I haven't really used Windows now for about three years.

On balance I'd rather use a wifi dongle than windows if that is the only option at present. Hopefully the ath9k driver is causing so many problems a fix will come out in the next release.

Regards

Wayne

---

### Post by hicksid on 2011-08-30
[/QUOTE]On balance I'd rather use a wifi dongle than windows if that is the only option at present. Hopefully the ath9k driver is causing so many problems a fix will come out in the next release.[/QUOTE]
 
Whats the best way to keep a track of new driver release ?

---

### Post by airper on 2011-08-30
I'm not exactly sure myself. I was planning to google it, check here and on the Mint forum. I would think we will see something on this given it is a fairly wide-spread problem right now.

I'm told that using Ubuntu 10.04 the wifi card works - see my other thread here: (last couple of posts)

[http://ubuntuforums.org/showthread.php?t=1821142&page=4](http://ubuntuforums.org/showthread.php?t=1821142&page=4)

Also Arch Linux has a fix for the ethernet issue for the Intel 82579v ethernet controller (not a problem for you I think, but certainly me and others). That gives me some hope that developers are on the case and looking for solutions, hopefully Ubuntu will pick them up quickly and implement them in the next release.

---

### Post by hicksid on 2011-08-31
OK, I'll keep checking back here for news.
 
Incidently, I had tried 10.04 of Ubuntu but with no luck.

---

### Post by airper on 2011-09-03
Hi Hicksid,

The Asus USB-N13 wifi dongle arrived yesterday £18 from Amazon UK. Following the instructions on the link above, I blacklistedthe rt2800usb driver and then rebooted. 

Much to my surprise you don't have to blacklist the ath9k driver. Both the N13 and the AR9285 show up in Network Manager's list, you just have to click on the right one and yep, it connected to the router no problems.

A decent internet connection at last. It is pretty fast as well.

Hope this helps

Best Regards

Wayne

---

### Post by hicksid on 2011-09-03
Hi Wayne,

Glad to hear of your success, odd that you dont have to blacklist the ath9k driver but hey, it works so good to go. I think I'm gonna wait until a fix comes out in 11.xx.

Cheers,
Ian

---

### Post by airper on 2011-09-30
Hi Hicksid,

Not sure if you have picked this up but an updated driver has been pushed out which  appears to be a very big step forwards.
                            
All my laptops with  new'ish Atheros wireless cards (AR9285 and AR928X) have a good working  wireless connection, which appears to be fast as well.

Hope this is helpful info to others, if you've been struggling with the ATH9K driver.

---

### Post by hicksid on 2011-09-30
Hi Wayne,

Many thanks for getting in touch about this - one question (a novice one) how do I get the driver onto my laptop ? Any and all help very much appreciated.
All the best,
idh

---

### Post by airper on 2011-10-01
Hi Ian,

All you need to do I think is install the latest updates via update manager. 

When I ran my updates it installed Kernel 2.6.38-11.50 which I think includes the updated drivers.

I only discovered this by accident. We have been out to Florida on Holiday, I did all the updates before we left. When I tried to connect to the router in the villa, it just linked up straight away.

I thought maybe it was the router, it was a Dlink one and unsecured, but we got back to UK and I just tried it at home on the BT router with WPA and it connected straight away.

Tried it on my other laptops which have new Atheros wireless cards and they all connected no problems.

Hope this helps.

Regards

Wayne

---

### Post by hicksid on 2011-10-01
Hi Wayne,

OK, nice and simple, so I did what you said and now we are in business via wireless !!

Many, many thanks for taking the time to post back to me on this whole subject.

All the best,
Ian

---

### Post by airper on 2011-10-01
No worries Ian, 

Glad it has worked for you as well. 

I think this is how Open Source is supposed to work. I get so much help from these forums, I'm pleased to be able to help someone else occasionally.

I'm not quite confident enough to launch into full support posts yet, but I do look at the new posts at least every few days and point a few others in the right direction if I can.

Great stuff.

Regards

Wayne

PS: you might want to mark this thread as solved, it might points others in the right direction too.

---

### Post by armando21 on 2012-05-26
Hello, guys Thank for this valuable information at the end I was able to update the  Kernel and my wireless card started working find. 
I also notice after testing all Karnel versions which I have installed from 

2.6.32.28
2.6.32.30
2.6.32.32
...........33
...........34
           35
           36
up to   41
I notice my internal wireless card worked at different speeds some of these Karnel versions the wireless signal were to  weak others were ok but also I tested an usb wireless card and in some versions of Karnel were automatic detectable by my computer  but other times not even appeared at the wireless connection utilities. 
there is some thing else I have a NETGEAR WG511T 108 Mbps Wireless PC Card I bought at ebay for $10 dollars. 
This PC Card works at any Karnel version. Well from 
2.6.32.28
up to
2.6.32.41
So far my Internet speed increase from 2Mbps internal wireless card (Atheros AR5001) to 20 Mbps with the PC Card.
So if you still have a problem with your internal wireless card I would recommend a PC Card. May be this would solve your problem once for all. 
I dont have a specific place to get this PC Card but look around and try it hopefully works for you too.

thanks  

By the way I have UBUNTU 10.04

Gracias y si desean mas informacion en espanol puedes mandarme un correo.

---


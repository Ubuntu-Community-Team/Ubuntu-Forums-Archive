---
title: "Jaunty ATI/AMD FGLRX driver install is broken :("
date: 2009-07-17
forum: Multimedia Software
---

### Post by hyperyoda on 2009-07-17
This is fresh Jaunty system, AMD Athlon dual core running kernel 2.6.28-11-generic #42-Ubuntu SMP

Have ATI Radeon HD graphics card.

Went to System->Administration->Hardware Drivers

It showed:

No proprietary drivers are in use on this system.
ATI/AMD proprietary FGLRX graphics driver

So I clicked Activate and it then it just hangs on:
Downloading and installing driver..0%

It never moves past 0% :( 

And my internet connection is working fine,no firewall in the way either.

How can I get this driver installed? I really need hardware acceleration so I can play games :)

Here is lspci output:

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
	Subsystem: Giga-byte Technology Device 21ae
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 2: Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
	Region 4: I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Vendor Specific Information <?>
	Kernel modules: fglrx

BTW: I noticed in that output it says:
Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]

But my ATI manual says it is supposed to have 512MB of dedicated video memory (DDR3) on the graphics card so what does lspci only show 256M?!

---

### Post by triphazard on 2009-07-18
Just thought I'd let the world know that I also have this problem.

I'm running an nVidia 8600GTS and the proprietary driver installer doesn't get past 0%.

I also have a working network connection and no firewall issues etc.

This OS was installed about half an hour ago and recently updated with security updates etc through the update manager.

Eventually this messsage comes up: -

Sorry, the Jockey backend crashed. Please file a bug at:
 ubuntu-bug jockey-common
Trying to recover by restarting backend.

---

### Post by markbuntu on 2009-07-18
You need to get all the updates before installing those drivers. Update, reboot and then you should be able to install them.

---

### Post by triphazard on 2009-07-19
> **markbuntu said:**
> You need to get all the updates before installing those drivers. Update, reboot and then you should be able to install them.

Sorry, I should have added that since getting all the updates the system has been rebooted; multiple times now actually.

Has anybody ever seen this before?

---

### Post by pme 72 on 2009-07-19
I recently installed an ATI HD4550 card in my AMD Athlon 3500+ running Jaunty 9.04. I got the message that proprietary drivers were available. When I checked Activate, they installed with no issues. 

desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

---

### Post by cottfcfan on 2009-07-19
I had the same problem, but found after a couple of minutes it will download and install.

---

### Post by hyperyoda on 2009-07-22
> **pme 72 said:**
> I recently installed an ATI HD4550 card in my AMD Athlon 3500+ running Jaunty 9.04. I got the message that proprietary drivers were available. When I checked Activate, they installed with no issues. 

desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

Fixed now :)

---

### Post by triphazard on 2009-07-27
Just to confirm, despite hyperyoda's being fixed, mine still does not work.

---

### Post by to6y on 2009-08-04
I have the same problem as triphazard. It says something about recovering after like an hour of being on 0%... I've updated and everything but it still won't budge. I really need a solution :(

---

### Post by markbuntu on 2009-08-06
> **to6y said:**
> I have the same problem as triphazard. It says something about recovering after like an hour of being on 0%... I've updated and everything but it still won't budge. I really need a solution :(

FYI it is doubtful that someone who can help you with your nvidia problem is going to look in a thread with ATI in the title. You have a different problem, you should start a new thread.

---


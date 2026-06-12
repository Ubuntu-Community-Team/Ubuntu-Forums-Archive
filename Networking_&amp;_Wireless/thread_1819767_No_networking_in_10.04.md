---
title: "No networking in 10.04"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by lhail on 2011-08-06
hi all
relatively new to ubuntu so bear with me please>
here is the synopsis of my problem.
Installed 10.04 on my daughters Dell inspiron laptop with no issues, all working fine>
I was travelling with business and came back to her not being able to connect to the internet> she"says" she deleted the network manager icon on the notification area ' by mistake'>

I tried today to add network manager, no joy either from add software or a terminal with sudo apt get, tried wired connection so I could update / install the packages required, no joy, eth0 is showing as unavailable>> so it appears this machine is disconnected from the outside world!
I tried ifconfig, however as alluded to, there are no network connections available for me to add or adjust. 

So I resorted to putting the ubuntu install disk into the cd drive, it doesn't want to mount that either!!
am I looking at a clean install?

sorry for the lack of information this got landed on my lap earlier today with little reliable background info> all help appreciated!

---

### Post by lkjoel on 2011-08-06
Could you give me the output of these Terminal commands?
```
uname -a
ifconfig
iwconfig
nm-tool
sudo /etc/init.d/networking restart
lspci -vvnn

```

---

### Post by omelette on 2011-08-06
Sounds to me like you just have a missing Notification applet itself - right-click the menu-bar, select Add to panel, and add the notifications applet.  This should not have effected your network connection itself though, just removed the icon(s)...

---

### Post by lhail on 2011-08-07
> **omelette said:**
> Sounds to me like you just have a missing Notification applet itself - right-click the menu-bar, select Add to panel, and add the notifications applet.  This should not have effected your network connection itself though, just removed the icon(s)...

No I thought of that and added a new notification applet, no network icon there either.

---

### Post by lhail on 2011-08-07
@ lkjoel, here you go..

**uname -a**
Linux claire-laptop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b4:55:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

**nm-tool**

NetworkManager Tool

State: disconnected


** (process:1581): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:1D:09:B4:55:73

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:1E:8C:4B:97:2C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

**sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                                                                                                [ OK ] 

I'll post the next command in another post as the result was long.

---

### Post by lhail on 2011-08-07
**lspci -vvnn**
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
	Latency: 64
	Kernel modules: ati-agp

00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 40000000-401fffff
	Prefetchable memory behind bridge: 0000000040200000-00000000403fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0200000-c02fffff
	Prefetchable memory behind bridge: 0000000040400000-00000000405fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] (prog-if 01)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at 8438 [size=8]
	Region 1: I/O ports at 8454 [size=4]
	Region 2: I/O ports at 8430 [size=8]
	Region 3: I/O ports at 8450 [size=4]
	Region 4: I/O ports at 8400 [size=16]
	Region 5: Memory at c0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] (prog-if 10)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] (prog-if 10)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] (prog-if 10)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] (prog-if 10)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at c0008000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] (prog-if 10)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at c0009000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] (prog-if 20)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 19
	Region 0: Memory at c0004400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Region 0: I/O ports at 8410 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 8420 [size=16]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Dell Device [1028:01f5]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
	Memory behind bridge: c0300000-c03fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
	Subsystem: Dell Device [1028:01f5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 9000 [size=256]
	Region 2: Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Device [1028:0007]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at c0300000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at c0302800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)
	Subsystem: Dell Device [1028:01f5]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 9
	Region 0: Memory at c0302c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: ricoh_mmc

---

### Post by lkjoel on 2011-08-07
Could you give me the output of these commands?
```
sudo modprobe b43
sudo modprobe b44
sudo nm-tool
sudo ifconfig
sudo iwconfig

```

---

### Post by lhail on 2011-08-07
**sudo modprobe b43 **
[sudo] password for claire:  

[B]sudo modprobe b44 
[/B]


**sudo nm-tool** 
 
NetworkManager Tool 
 
State: disconnected 
 
 
** (process:1443): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings: 
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            b44 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1D:09:B4:55:73 
 
  Capabilities: 
    Carrier Detect:  yes 
    Speed:           10 Mb/s 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            b43 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1E:8C:4B:97:2C 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points  

**sudo ifconfig **
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b4:55:73   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
[B]
sudo iwconfig[/B] 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off

---

### Post by lkjoel on 2011-08-07
Do you want to fix wired or wireless first?

---

### Post by lhail on 2011-08-07
well my daughter will use wireless most, but I suppose for a fall back I'll need wired too!!

thanks for your help btw :)

---

### Post by lhail on 2011-08-08
> **lkjoel said:**
> Do you want to fix wired or wireless first?

Wireless first please

---

### Post by lkjoel on 2011-08-08
Could you give me the output of this command?
```
cat /etc/network/interfaces 

```

---

### Post by lhail on 2011-08-08
auto lo
iface lo inet loopback

---

### Post by lkjoel on 2011-08-08
Good, that file is not corrupted.

Could you give me the output of these commands (in order):
```
sudo modprobe b43
sudo modprobe b44
sudo modprobe ssb
sudo nm-tool
sudo ifconfig
sudo iwconfig

```

---

### Post by lhail on 2011-08-08
**sudo modprobe b43** 
[sudo] password for claire:  
claire@claire-laptop:~$ **sudo modprobe b44 **
claire@claire-laptop:~$ **sudo nm-tool** 
 
NetworkManager Tool 
 
State: disconnected 
 
 
** (process:2505): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings: 
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            b44 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1D:09:B4:55:73 
 
  Capabilities: 
    Carrier Detect:  yes 
    Speed:           10 Mb/s 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            b43 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1E:8C:4B:97:2C 
 
  Capabilities: 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points  
 
 
claire@claire-laptop:~$ **sudo ifconfig **
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b4:55:73   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
 
claire@claire-laptop:~$ **sudo iwconfig** 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off

---

### Post by lhail on 2011-08-08
didn't I already send that info yesterday tho?

---

### Post by lkjoel on 2011-08-08
Yes you did send that info, but we did a few system changes, and I wanted to see if they worked.
They didn't work unfortunately.

Have you tried rebooting?

---

### Post by lhail on 2011-08-08
yes the system has been rebooted a few times over the past few days with the same problem remaining

---

### Post by lkjoel on 2011-08-08
Try this:
```
sudo apt-get update; sudo apt-get dist-upgrade
sudo apt-get install firmware-b43-installer

```Then reboot

---

### Post by lhail on 2011-08-08
> **lkjoel said:**
> Try this:
```
sudo apt-get update; sudo apt-get dist-upgrade
sudo apt-get install firmware-b43-installer

```Then reboot

I'll try, but I already tried installing NM that way and because there is no network connection it fails

---

### Post by lhail on 2011-08-08
claire@claire-laptop:~$ sudo apt-get update; sudo apt-get dist-upgrade 
[sudo] password for claire:  
Err [http://archive.monubuntu.fr](http://archive.monubuntu.fr) lucid-updates Release.gpg 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                              
  Could not resolve 'archive.canonical.com' 
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US        
  Could not resolve 'archive.canonical.com' 
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                        
  Could not resolve 'dl.google.com' 
Err [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US 
  Could not resolve 'dl.google.com' 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_US 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/) lucid/main Translation-en_US 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US 
  Could not resolve 'ppa.launchpad.net' 
Err [http://archive.monubuntu.fr/](http://archive.monubuntu.fr/) lucid-updates/main Translation-en_US 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr/](http://archive.monubuntu.fr/) lucid-updates/restricted Translation-en_US 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr](http://archive.monubuntu.fr) lucid-security Release.gpg 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr/](http://archive.monubuntu.fr/) lucid-security/main Translation-en_US 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr/](http://archive.monubuntu.fr/) lucid-security/restricted Translation-en_US 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr](http://archive.monubuntu.fr) lucid-proposed Release.gpg 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr/](http://archive.monubuntu.fr/) lucid-proposed/restricted Translation-en_US 
  Could not resolve 'archive.monubuntu.fr' 
Err [http://archive.monubuntu.fr/](http://archive.monubuntu.fr/) lucid-proposed/main Translation-en_US 
  Could not resolve 'archive.monubuntu.fr' 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid Release.gpg 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main Translation-en_US 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted Translation-en_US 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid Release 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid/main Packages 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid/restricted Packages 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid/main Packages 
Ign cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid/restricted Packages 
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid/main Packages 
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Err cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1) lucid/restricted Packages 
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Reading package lists... Done 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-updates/Release.gpg](http://archive.monubuntu.fr/dists/lucid-updates/Release.gpg)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://archive.monubuntu.fr/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://archive.monubuntu.fr/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'archive.canonical.com' 
 
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-security/Release.gpg](http://archive.monubuntu.fr/dists/lucid-security/Release.gpg)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://archive.monubuntu.fr/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://archive.monubuntu.fr/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-proposed/Release.gpg](http://archive.monubuntu.fr/dists/lucid-proposed/Release.gpg)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-proposed/restricted/i18n/Translation-en_US.bz2](http://archive.monubuntu.fr/dists/lucid-proposed/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://archive.monubuntu.fr/dists/lucid-proposed/main/i18n/Translation-en_US.bz2](http://archive.monubuntu.fr/dists/lucid-proposed/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.monubuntu.fr' 
 
W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Could not resolve 'dl.google.com' 
 
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2)  Could not resolve 'dl.google.com' 
 
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net' 
 
W: Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 
W: Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 
W: Some index files failed to download, they have been ignored, or old ones used instead. 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
The following packages will be upgraded: 
  google-chrome-stable wine1.3-gecko winetricks wisotool 
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 45.3MB of archives. 
After this operation, 12.4MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main wine1.3-gecko 1.2.0-0ubuntu1~maverickppa1 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main winetricks 0.0+20110312-0ubuntu1~ppa1 
  Could not resolve 'ppa.launchpad.net' 
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main wisotool 0.0+20110312-0ubuntu1~ppa1 
  Could not resolve 'ppa.launchpad.net' 
Err [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main google-chrome-stable 10.0.648.151-r78498 
  Could not resolve 'dl.google.com' 
Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_10.0.648.151-r78498_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_10.0.648.151-r78498_i386.deb)  Could not resolve 'dl.google.com' 
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3-gecko/wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3-gecko/wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb)  Could not resolve 'ppa.launchpad.net' 
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/winetricks/winetricks_0.0+20110312-0ubuntu1~ppa1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/winetricks/winetricks_0.0+20110312-0ubuntu1~ppa1_i386.deb)  Could not resolve 'ppa.launchpad.net' 
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/winetricks/wisotool_0.0+20110312-0ubuntu1~ppa1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/winetricks/wisotool_0.0+20110312-0ubuntu1~ppa1_i386.deb)  Could not resolve 'ppa.launchpad.net' 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
claire@claire-laptop:~$ sudo apt-get install firmware-b43-installer 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
E: Couldn't find package firmware-b43-installer

---

### Post by lkjoel on 2011-08-08
Right, I forgot you couldn't download things lol!
Sadly, firmware-b43-installer is not available for 10.04.

I'll call in wildmanne39, and see if he can help you.

---

### Post by lhail on 2011-08-08
> **lkjoel said:**
> Right, I forgot you couldn't download things lol!
Sadly, firmware-b43-installer is not available for 10.04.

I'll call in wildmanne39, and see if he can help you.

thanks for the help:)

---

### Post by wildmanne39 on 2011-08-08
Hi, please post the results of these commands.
```
cat /etc/modprobe.d/blacklist.conf
```
```
lsmod | grep b43
```
```
dmesg | grep b43
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
Thank you

---


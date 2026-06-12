---
title: "Network adapters State: disconnected"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by brendencm on 2011-07-05
Hi, I have been managing a Solaris system and am migrating it over to Ubuntu. I can't for the life of me 
figure out how to get these cards up. First I installed 10.10 (under the Live CD which came with a book) 
and had a network connection for a day or so. I then decided to install 11.04 alternate and havent been 
able to get the network up. Initially I tried to set up a static ip address but was getting all sorts of 
SIOCSIFFLAGS errors when I tried to plumb the devices. This lead me to find that the interfaces in 
both adapters I have are inactive, disconnected and
unavalible depending on which command you use. To make things simple I switched to dhcp. It looks like 
I am getting an interup error on the e1000. But I still dont know why the BroadComm doesnt come up.

Also I found something about a em driver for the Intel card instad of the e1000 driver. 
[http://manpages.ubuntu.com/manpages/natty/man4/em.4freebsd.html](http://manpages.ubuntu.com/manpages/natty/man4/em.4freebsd.html)
where is the kernel configuration file and the loader.conf file?

Also,
The Devices-NetworkTools GUI Under interface information has State: Inactive for all adapters.   

Any help would be great!! I have included output from several commands-

nm-tool:

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        00:04:23:CA:E2:34

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000
  State:             unavailable
  Default:           no
  HW Address:        00:04:23:CA:E2:35

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth3 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:E0:81:31:FE:EE

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth2 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:E0:81:31:FE:EF

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


 
cat /etc/network/interfaces :

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto eth3
iface eth3 inet dhcp


lsmod | grep e1000 :
e1000                 111862  0

lsmod | grep tg3 :
lsmod | grep tg3
tg3                   141750  0
dmesg | grep e1000 :
[    0.948438] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    0.948441] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    1.038391] e1000 0000:19:03.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    1.370928] e1000 0000:19:03.0: eth1: (PCI-X:133MHz:64-bit) 00:04:23:ca:e2:34
[    1.370934] e1000 0000:19:03.0: eth1: Intel(R) PRO/1000 Network Connection
[    1.370987] e1000 0000:19:03.1: PCI INT B -> GSI 24 (level, low) -> IRQ 24
[    1.701020] e1000 0000:19:03.1: eth3: (PCI-X:133MHz:64-bit) 00:04:23:ca:e2:35
[    1.701025] e1000 0000:19:03.1: eth3: Intel(R) PRO/1000 Network Connection
[   15.210130] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[   16.887187] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[   16.925856] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[   16.966317] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[   33.211872] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[   33.259746] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[   77.292407] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22c
[   77.336012] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[  426.230724] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[  450.238207] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[  769.233257] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[  866.230712] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[ 1214.238184] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[ 1348.233135] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[ 1667.237321] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[ 1799.232240] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[ 1905.235621] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
[ 2065.233195] e1000 0000:19:03.1: eth1: Unable to allocate interrupt Error: -22
[ 2273.231149] e1000 0000:19:03.0: eth0: Unable to allocate interrupt Error: -22
dmesg | grep tg3 :
[    1.044288] tg3.c:v3.116 (December 3, 2010)
[    1.044298] tg3 0000:1a:09.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    1.327630] tg3 0000:1a:09.0: eth0: Tigon3 [partno(BCM95704A7) rev 2003] (PCIX:100MHz:64-bit) MAC address 00:e0:81:31:fe:ee
[    1.327635] tg3 0000:1a:09.0: eth0: attached PHY is 5704 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.327638] tg3 0000:1a:09.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.327641] tg3 0000:1a:09.0: eth0: dma_rwctrl[769f4000] dma_mask[64-bit]
[    1.327718] tg3 0000:1a:09.1: PCI INT B -> GSI 29 (level, low) -> IRQ 29
[    1.371749] tg3 0000:1a:09.1: eth2: Tigon3 [partno(BCM95704A7) rev 2003] (PCIX:100MHz:64-bit) MAC address 00:e0:81:31:fe:ef
[    1.371753] tg3 0000:1a:09.1: eth2: attached PHY is 5704 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.371757] tg3 0000:1a:09.1: eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.371759] tg3 0000:1a:09.1: eth2: dma_rwctrl[769f4000] dma_mask[64-bit]


lspci -k :
19:03.0 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
	Subsystem: Intel Corporation PRO/1000 MT Dual Port Server Adapter
	Kernel driver in use: e1000
	Kernel modules: e1000
19:03.1 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
	Subsystem: Intel Corporation PRO/1000 MT Dual Port Server Adapter
	Kernel driver in use: e1000
	Kernel modules: e1000
1a:09.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)
	Subsystem: Broadcom Corporation Device 1644
	Kernel driver in use: tg3
	Kernel modules: tg3
1a:09.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)
	Subsystem: Broadcom Corporation Device 1644
	Kernel driver in use: tg3
	Kernel modules: tg3

lspci -vv :
19:03.0 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
	Subsystem: Intel Corporation PRO/1000 MT Dual Port Server Adapter
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (63750ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 27
	Region 0: Memory at d8120000 (64-bit, non-prefetchable) [size=128K]
	Region 2: Memory at d8140000 (64-bit, non-prefetchable) [size=256K]
	Region 4: I/O ports at 3800 [size=64]
	[virtual] Expansion ROM at d8380000 [disabled] [size=256K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [e4] PCI-X non-bridge device
		Command: DPERE- ERO+ RBC=2048 OST=1
		Status: Dev=19:03.0 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
	Capabilities: [f0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: e1000
	Kernel modules: e1000

19:03.1 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
	Subsystem: Intel Corporation PRO/1000 MT Dual Port Server Adapter
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (63750ns min), Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 24
	Region 0: Memory at d81c0000 (64-bit, non-prefetchable) [size=128K]
	Region 2: Memory at d8180000 (64-bit, non-prefetchable) [size=256K]
	Region 4: I/O ports at 3840 [size=64]
	[virtual] Expansion ROM at d83c0000 [disabled] [size=256K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [e4] PCI-X non-bridge device
		Command: DPERE- ERO+ RBC=2048 OST=1
		Status: Dev=19:03.1 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
	Capabilities: [f0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Kernel driver in use: e1000
	Kernel modules: e1000

1a:09.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)
	Subsystem: Broadcom Corporation Device 1644
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (16000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at d8210000 (64-bit, non-prefetchable) [size=64K]
	Region 2: Memory at d8200000 (64-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d8400000 [disabled] [size=64K]
	Capabilities: [40] PCI-X non-bridge device
		Command: DPERE- ERO+ RBC=2048 OST=1
		Status: Dev=1a:09.0 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
		Product Name: Broadcom Gigabit Ethernet Controller
		Read-only fields:
			[PN] Part number: BCM95704A7
			[EC] Engineering changes: 107070-26
			[SN] Serial number: 0123456789
			[MN] Manufacture ID: 31 34 35 35
			[RV] Reserved: checksum bad, 36 byte(s) reserved
		Read/write fields:
			[YA] Asset tag: XYZ11334455
			[RW] Read-write area: 107 byte(s) free
		End
	Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
		Address: 2008001060080000  Data: 0c04
	Kernel driver in use: tg3
	Kernel modules: tg3

1a:09.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)
	Subsystem: Broadcom Corporation Device 1644
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (16000ns min), Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 29
	Region 0: Memory at d8230000 (64-bit, non-prefetchable) [size=64K]
	Region 2: Memory at d8220000 (64-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d8410000 [disabled] [size=64K]
	Capabilities: [40] PCI-X non-bridge device
		Command: DPERE- ERO+ RBC=2048 OST=1
		Status: Dev=1a:09.1 64bit+ 133MHz+ SCD- USC- DC=simple DMMRBC=2048 DMOST=1 DMCRS=16 RSCEM- 266MHz- 533MHz-
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [50] Vital Product Data
		Product Name: Broadcom Gigabit Ethernet Controller
		Read-only fields:
			[PN] Part number: BCM95704A7
			[EC] Engineering changes: 107070-26
			[SN] Serial number: 0123456789
			[MN] Manufacture ID: 31 34 35 35
			[RV] Reserved: checksum bad, 36 byte(s) reserved
		Read/write fields:
			[YA] Asset tag: XYZ11334455
			[RW] Read-write area: 107 byte(s) free
		End
	Capabilities: [58] MSI: Enable- Count=1/8 Maskable- 64bit+
		Address: 0b1686ef823801c8  Data: 0000
	Kernel driver in use: tg3
	Kernel modules: tg3

modinfo e1000
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/e1000/e1000.ko
version:        7.3.21-k8-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     E005D763BC7910379BDD09A
alias:          pci:v00008086d00002E6Esv*sd*bc*sc*i*
alias:          pci:v00008086d000010B5sv*sd*bc*sc*i*
alias:          pci:v00008086d00001099sv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001079sv*sd*bc*sc*i*
alias:          pci:v00008086d00001078sv*sd*bc*sc*i*
alias:          pci:v00008086d00001077sv*sd*bc*sc*i*
alias:          pci:v00008086d00001076sv*sd*bc*sc*i*
alias:          pci:v00008086d00001075sv*sd*bc*sc*i*
alias:          pci:v00008086d00001028sv*sd*bc*sc*i*
alias:          pci:v00008086d00001027sv*sd*bc*sc*i*
alias:          pci:v00008086d00001026sv*sd*bc*sc*i*
alias:          pci:v00008086d0000101Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000101Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000101Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001019sv*sd*bc*sc*i*
alias:          pci:v00008086d00001018sv*sd*bc*sc*i*
alias:          pci:v00008086d00001017sv*sd*bc*sc*i*
alias:          pci:v00008086d00001016sv*sd*bc*sc*i*
alias:          pci:v00008086d00001015sv*sd*bc*sc*i*
alias:          pci:v00008086d00001014sv*sd*bc*sc*i*
alias:          pci:v00008086d00001013sv*sd*bc*sc*i*
alias:          pci:v00008086d00001012sv*sd*bc*sc*i*
alias:          pci:v00008086d00001011sv*sd*bc*sc*i*
alias:          pci:v00008086d00001010sv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000100Csv*sd*bc*sc*i*
alias:          pci:v00008086d00001009sv*sd*bc*sc*i*
alias:          pci:v00008086d00001008sv*sd*bc*sc*i*
alias:          pci:v00008086d00001004sv*sd*bc*sc*i*
alias:          pci:v00008086d00001001sv*sd*bc*sc*i*
alias:          pci:v00008086d00001000sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
parm:           TxDescriptors:Number of transmit descriptors (array of int)
parm:           RxDescriptors:Number of receive descriptors (array of int)
parm:           Speed:Speed setting (array of int)
parm:           Duplex:Duplex setting (array of int)
parm:           AutoNeg:Advertised auto-negotiation setting (array of int)
parm:           FlowControl:Flow Control setting (array of int)
parm:           XsumRX:Disable or enable Receive Checksum offload (array of int)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           debug:Debug level (0=none,...,16=all) (int)

modinfo tg3
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/tg3.ko
firmware:       tigon/tg3_tso5.bin
firmware:       tigon/tg3_tso.bin
firmware:       tigon/tg3.bin
version:        3.116
license:        GPL
description:    Broadcom Tigon3 ethernet driver
author:         David S. Miller (davem@redhat.com) and Jeff Garzik (jgarzik@pobox.com)
srcversion:     B99732A673648F3B09C3BDB
alias:          pci:v0000106Bd00001645sv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003EAsv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003EBsv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003E9sv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003E8sv*sd*bc*sc*i*
alias:          pci:v00001148d00004500sv*sd*bc*sc*i*
alias:          pci:v00001148d00004400sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001657sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B6sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B2sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B4sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B0sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B5sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B1sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001656sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001655sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001691sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001694sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001690sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001692sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A0sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001699sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001689sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001688sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001680sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001681sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001684sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001698sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001713sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001712sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016DDsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001679sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001678sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001669sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001668sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Fsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001693sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001674sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001673sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001672sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Asv*sd*bc*sc*i*
alias:          pci:v000014E4d000016FEsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016FDsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016F7sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001601sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001600sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001677sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001659sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Esv*sd*bc*sc*i*
alias:          pci:v000014E4d00001649sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000170Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000170Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00001696sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016C7sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016C6sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A8sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A7sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A6sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001654sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001653sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000164Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001648sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001647sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001646sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001645sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001644sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 
parm:           tg3_debug:Tigon3 bitmapped debugging message enable value (int)

---

### Post by brendencm on 2011-07-05
I should add.... these are all wired devices.

---


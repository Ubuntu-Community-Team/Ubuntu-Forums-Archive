---
title: "Battling with Dvico TV Tuner again"
date: 2010-06-25
forum: Multimedia Software
---

### Post by Dionikon on 2010-06-25
So I've rebuilt my Mythbuntu box.  I'm trying to set up 2 tuner cards and... just like last time I did this, 1 works, 1 doesn't.

I have never managed to get this PCIe card working and have previously given up and stuck with only 1 tuner.  I have now rebuilt with Mythbuntu version 10.04, hoping that things may be different, it appears not unfortunately.

Some details:

I have 2 cards, one is PCI, and one is PCIe, both are Dvico Fusion cards.

The working card is a Dvico Fusion DVB-T Pro (PCI).  And the non working is a Dvico Fusion DVB-T Plus (PCIe).

The working card detects as a Zarlink ZL10353 DVB-T but works perfectly as far as I can tell.

I have followed the various tutorials on installing the V4L drivers, then copied the required firmware and no joy.

This is the tutorial I followed: 
[http://ubuntuforums.org/showthread.php?t=1253586](http://ubuntuforums.org/showthread.php?t=1253586)

dmesg output:
```

[   13.652287] cx23885 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   13.652291] cx23885[0]: Your board isn't known (yet) to the driver.
[   13.652292] cx23885[0]: Try to pick one of the existing card configs via
[   13.652293] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   13.652295] cx23885[0]: version might help as well.
[   13.652296] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   13.652298] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   13.652300] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   13.652302] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   13.652303] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   13.652305] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   13.652306] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   13.652308] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   13.652310] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   13.652311] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   13.652313] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   13.652315] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   13.652316] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   13.652318] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   13.652320] cx23885[0]:    card=13 -> Compro VideoMate E650F
[   13.652322] cx23885[0]:    card=14 -> TurboSight TBS 6920
[   13.652323] cx23885[0]:    card=15 -> TeVii S470
[   13.652325] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[   13.652327] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[   13.652328] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[   13.652330] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[   13.652331] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[   13.652333] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[   13.652335] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[   13.652336] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[   13.652338] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[   13.652340] cx23885[0]:    card=25 -> Compro VideoMate E800
[   13.652378] CORE cx23885[0]: subsystem: 18ac:db30, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.689483] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   13.689489] nvidia 0000:02:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
[   13.689497] nvidia 0000:02:00.0: setting latency timer to 64
[   13.689502] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.690317] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   13.691536] lp0: using parport0 (interrupt-driven).
[   13.758110] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   13.758463] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   13.758471]   alloc irq_desc for 17 on node -1
[   13.758473]   alloc kstat_irqs on node -1
[   13.758482] cx8800 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   13.758721] cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected], frontend(s): 1
[   13.758723] cx88[0]: TV tuner type 4, Radio tuner type -1
[   13.760742] ppdev: user-space parallel port driver
[   13.761520] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-9/2-9:1.0/input/input5
[   13.761592] logitech 0003:046D:C30A.0003: input,hidraw3: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:04.0-9/input0
[   13.778649] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   13.792190] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   13.792199] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xe9000000
[   13.792206] cx23885 0000:03:00.0: setting latency timer to 64
[   13.792210] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.796382] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:04.0/usb2/2-9/2-9:1.1/input/input6
[   13.796502] logitech 0003:046D:C30A.0004: input,hidraw4: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:04.0-9/input1
[   13.807103] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-4/2-4.3/2-4.3:1.0/input/input7
[   13.807263] logitech 0003:046D:C71F.0006: input,hiddev97,hidraw5: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-4.3/input0
[   13.830948] Console: switching to colour frame buffer device 80x30
[   13.832142] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   13.925223] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 17, latency: 32, mmio: 0xe6000000
[   13.925235] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.925440] cx88[0]/0: registered device video0 [v4l2]
[   13.925526] cx88[0]/0: registered device vbi0
[   13.925582] cx88[0]/2: cx2388x 8802 Driver Manager
[   13.925599] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   13.925607] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 17, latency: 32, mmio: 0xe7000000
[   13.925611] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.945685] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   13.945689] cx88/2: registering cx8802 driver, type: dvb access: shared
[   13.945692] cx88[0]/2: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21]
[   13.945695] cx88[0]/2: cx2388x based DVB/ATSC card
[   13.945698] cx8802_alloc_frontends() allocating 1 frontend(s)
[   13.961316] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   13.961583] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   13.961589] HDA Intel 0000:00:09.0: PCI INT A -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   13.961592] hda_intel: Disable MSI for Nvidia chipset
[   13.961618] HDA Intel 0000:00:09.0: setting latency timer to 64
[   13.977941] DVB: registering new adapter (cx88[0])
[   13.977946] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   14.509121] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:09.0/input/input8
[   23.744159] eth0: no IPv6 routers present

```

lspci:
```

00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 SATA controller: nVidia Corporation GeForce 7100/nForce 630i SATA (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)

```

lspci -vv:
```

non working card:
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: DViCO Corporation Device db10
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e6000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx8800
	Kernel modules: cx8800

01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: DViCO Corporation Device db10
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (1500ns min, 22000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

working card:
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
	Subsystem: DViCO Corporation Device db30
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e9000000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data <?>
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [200] Virtual Channel <?>
	Kernel driver in use: cx23885
	Kernel modules: cx23885

```

So where to next?  I don't have another PCI slot in this motherboard so changing the card to PCI is not really an option.

---

### Post by Dionikon on 2010-06-27
Well, after 2 days of messing around I still don't have a solution.  I have however stumbled across another potential cause of my problems.

I have attempted to install Chris Pascoe's Dvico Linux drivers which should support both versions of my card and discovered an error occurs during the "make" phase.

This is the process I followed:

[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

When I run "make" I get an error.

Here is the output:

```

root@alma:/opt/source/xc-test# make
make -C /opt/source/xc-test/v4l 
make[1]: Entering directory `/opt/source/xc-test/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.32-22-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
Kernel build directory is /lib/modules/2.6.32-22-generic/build
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/opt/source/xc-test/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /opt/source/xc-test/v4l/flexcop-pci.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-usb.o
  CC [M]  /opt/source/xc-test/v4l/flexcop.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-fe-tuner.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-i2c.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-sram.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-eeprom.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-misc.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-hw-filter.o
  CC [M]  /opt/source/xc-test/v4l/flexcop-dma.o
  CC [M]  /opt/source/xc-test/v4l/bttv-driver.o
In file included from /opt/source/xc-test/v4l/bttvp.h:60,
                 from /opt/source/xc-test/v4l/bttv-driver.c:46:
/opt/source/xc-test/v4l/bttv.h:313: error: 'BUS_ID_SIZE' undeclared here (not in a function)
In file included from /opt/source/xc-test/v4l/bttv-driver.c:46:
/opt/source/xc-test/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/percpu.h:45,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/current.h:5,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /opt/source/xc-test/v4l/bttv-driver.c:38:
include/linux/kernel.h:579:1: warning: this is the location of the previous definition
/opt/source/xc-test/v4l/bttv-driver.c: In function 'show_card':
/opt/source/xc-test/v4l/bttv-driver.c:182: error: 'struct video_device' has no member named 'class_dev'
/opt/source/xc-test/v4l/bttv-driver.c:182: warning: type defaults to 'int' in declaration of '__mptr'
/opt/source/xc-test/v4l/bttv-driver.c:182: warning: initialization from incompatible pointer type
/opt/source/xc-test/v4l/bttv-driver.c:182: error: 'struct video_device' has no member named 'class_dev'
/opt/source/xc-test/v4l/bttv-driver.c:183: error: incompatible type for argument 1 of 'dev_get_drvdata'
include/linux/device.h:494: note: expected 'const struct device *' but argument is of type 'struct device'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'audio_mux':
/opt/source/xc-test/v4l/bttv-driver.c:1255: error: 'VIDIOC_INT_S_AUDIO_ROUTING' undeclared (first use in this function)
/opt/source/xc-test/v4l/bttv-driver.c:1255: error: (Each undeclared identifier is reported only once
/opt/source/xc-test/v4l/bttv-driver.c:1255: error: for each function it appears in.)
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_common_ioctls':
/opt/source/xc-test/v4l/bttv-driver.c:1875: error: implicit declaration of function 'v4l2_video_std_construct'
/opt/source/xc-test/v4l/bttv-driver.c:2024: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c:2024: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c:2024: error: too many arguments to function 'v4l2_chip_match_host'
/opt/source/xc-test/v4l/bttv-driver.c:2027: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c:2029: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c:2029: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c:2031: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c:2031: error: dereferencing pointer to incomplete type
/opt/source/xc-test/v4l/bttv-driver.c: In function 'setup_window':
/opt/source/xc-test/v4l/bttv-driver.c:2324: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2341: error: implicit declaration of function 'videobuf_pci_alloc'
/opt/source/xc-test/v4l/bttv-driver.c:2341: warning: assignment makes pointer from integer without a cast
/opt/source/xc-test/v4l/bttv-driver.c:2346: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_s_fmt':
/opt/source/xc-test/v4l/bttv-driver.c:2527: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2536: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_do_ioctl':
/opt/source/xc-test/v4l/bttv-driver.c:2564: error: implicit declaration of function 'v4l_print_ioctl'
/opt/source/xc-test/v4l/bttv-driver.c:2587: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2599: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2723: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2726: warning: assignment makes pointer from integer without a cast
/opt/source/xc-test/v4l/bttv-driver.c:2734: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2769: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:2795: warning: assignment makes pointer from integer without a cast
/opt/source/xc-test/v4l/bttv-driver.c:2801: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3008: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3026: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3047: error: implicit declaration of function 'v4l_compat_translate_ioctl'
/opt/source/xc-test/v4l/bttv-driver.c:3053: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_ioctl':
/opt/source/xc-test/v4l/bttv-driver.c:3064: error: implicit declaration of function 'video_usercopy'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_read':
/opt/source/xc-test/v4l/bttv-driver.c:3076: error: 'v4l2_type_names' undeclared (first use in this function)
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_poll':
/opt/source/xc-test/v4l/bttv-driver.c:3120: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3124: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3127: warning: assignment makes pointer from integer without a cast
/opt/source/xc-test/v4l/bttv-driver.c:3129: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3137: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c:3143: error: 'struct videobuf_queue' has no member named 'lock'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_open':
/opt/source/xc-test/v4l/bttv-driver.c:3182: error: 'v4l2_type_names' undeclared (first use in this function)
/opt/source/xc-test/v4l/bttv-driver.c:3194: error: implicit declaration of function 'videobuf_queue_pci_init'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_mmap':
/opt/source/xc-test/v4l/bttv-driver.c:3276: error: 'v4l2_type_names' undeclared (first use in this function)
/opt/source/xc-test/v4l/bttv-driver.c: At top level:
/opt/source/xc-test/v4l/bttv-driver.c:3288: error: 'v4l_compat_ioctl32' undeclared here (not in a function)
/opt/source/xc-test/v4l/bttv-driver.c:3299: error: unknown field 'type' specified in initializer
/opt/source/xc-test/v4l/bttv-driver.c:3301: warning: initialization from incompatible pointer type
/opt/source/xc-test/v4l/bttv-driver.c:3308: error: unknown field 'type' specified in initializer
/opt/source/xc-test/v4l/bttv-driver.c:3309: warning: initialization from incompatible pointer type
/opt/source/xc-test/v4l/bttv-driver.c: In function 'radio_open':
/opt/source/xc-test/v4l/bttv-driver.c:3340: error: 'AUDC_SET_RADIO' undeclared (first use in this function)
/opt/source/xc-test/v4l/bttv-driver.c: At top level:
/opt/source/xc-test/v4l/bttv-driver.c:3463: error: unknown field 'type' specified in initializer
/opt/source/xc-test/v4l/bttv-driver.c:3464: warning: initialization from incompatible pointer type
/opt/source/xc-test/v4l/bttv-driver.c: In function 'vdev_init':
/opt/source/xc-test/v4l/bttv-driver.c:4006: error: incompatible types when assigning to type 'struct device' from type 'struct device *'
/opt/source/xc-test/v4l/bttv-driver.c: In function 'bttv_register_video':
/opt/source/xc-test/v4l/bttv-driver.c:4044: error: 'struct video_device' has no member named 'type'
/opt/source/xc-test/v4l/bttv-driver.c:4057: error: 'struct video_device' has no member named 'class_dev'
make[3]: *** [/opt/source/xc-test/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/opt/source/xc-test/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/opt/source/xc-test/v4l'
make: *** [all] Error 2

```

It seems that the make output is complaining about the kernel version, which it should, I am not running 2.6.32-22-generic, I am running 2.6.32-23-generic (according to uname -a and cat /proc/version).

What should I do to get these drivers compiled and installed???

---


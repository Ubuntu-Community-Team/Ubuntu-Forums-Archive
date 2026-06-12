---
title: "sound issues with lynx"
date: 2010-05-29
forum: Multimedia Software
---

### Post by linuxnoob40 on 2010-05-29
sound worked fine on the previous build but is totally fubared on this one.
what i have discovered so far which may or may not help is 
1: upon booting up i see an error flash across the screen something about "nforce error probing sb1"
now upon a fresh boot up i have sound and it will stay depending on what i do but the problems seem to happen when im streaming audio. anyhow when it quits i get this in my logfile 


[  287.232020] ALSA pcm.c:300: setting usb interface 2:1
 [  287.232025] ALSA pcm.c:174: 4:2:1: endpoint lacks sample rate attribute bit, cannot set.
 [  287.243995] ALSA pcm.c:300: setting usb interface 2:1
 [  287.243999] ALSA pcm.c:174: 4:2:1: endpoint lacks sample rate attribute bit, cannot set.

i don't know what else to put in here that will help. so let me know what i can post that will help. this is driving me crazy cuz i have to reboot to get sound back after this happens.

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by linuxnoob40 on 2010-05-30
ok 

>  uname -a
Linux steven-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



> cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 21 2010 for kernel 2.6.32-22-generic (SMP).







>  head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory





as for the make of my system i put it together myself
mb:Abit P5N-T DELUXE
mem : 2gig dual channel kingston ram i forget the speed 
proc: intel core 2 duo 2.53 gig 
sound:sound blaster audigy gamer 
video: nvidia gforce 9600 GT

---

### Post by linuxnoob40 on 2010-05-30
can anyone fix this or do i have to reinstall from scratch?

---

### Post by linuxnoob40 on 2010-05-31
Bunmp

---

### Post by lidex on 2010-05-31
Please use code tags for these outputs:
```
lspci -vv
lsusb
lsmod
```

---

### Post by linuxnoob40 on 2010-05-31
here ya go its long


> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=0
	I/O behind bridge: 0000b000-0000cfff
	Memory behind bridge: e8000000-edffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 255
	Region 0: I/O ports at ff00 [size=64]
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c80 [size=64]
	Capabilities: <access denied>
	Kernel modules: i2c-nforce2

00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at effff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at efffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at fc00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 23
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at f700 [size=16]
	Region 5: Memory at efffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 22
	Region 0: I/O ports at 09e0 [size=8]
	Region 1: I/O ports at 0be0 [size=4]
	Region 2: I/O ports at 0960 [size=8]
	Region 3: I/O ports at 0b60 [size=4]
	Region 4: I/O ports at f200 [size=16]
	Region 5: Memory at efffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin C routed to IRQ 21
	Region 0: I/O ports at f100 [size=8]
	Region 1: I/O ports at f000 [size=4]
	Region 2: I/O ports at ef00 [size=8]
	Region 3: I/O ports at ee00 [size=4]
	Region 4: I/O ports at ed00 [size=16]
	Region 5: Memory at efffb000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efd00000-efdfffff
	Prefetchable memory behind bridge: efe00000-efefffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn+
	Capabilities: <access denied>

00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 26
	Region 0: Memory at efffa000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at ec00 [size=8]
	Region 2: Memory at efff9000 (32-bit, non-prefetchable) [size=256]
	Region 3: Memory at efff8000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: efc00000-efcfffff
	Prefetchable memory behind bridge: 00000000efb00000-00000000efbfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=01, secondary=02, subordinate=04, sec-latency=0
	I/O behind bridge: 0000b000-0000cfff
	Memory behind bridge: e8000000-edffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e8000000-ebffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: edf00000-edffffff
	Prefetchable memory behind bridge: 00000000dff00000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
	Subsystem: eVga.com. Corp. Device c861
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at ea000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at e8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at cf00 [size=128]
	[virtual] Expansion ROM at ebf80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidia-173, nvidiafb, nouveau

05:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0051
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at df00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

05:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs Device 0040
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Region 0: I/O ports at de00 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

05:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at efdff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at efdf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

05:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 81fe
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at efdfe000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at dd00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 6121
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at af00 [size=8]
	Region 1: I/O ports at ae00 [size=4]
	Region 2: I/O ports at ad00 [size=8]
	Region 3: I/O ports at ac00 [size=4]
	Region 4: I/O ports at ab00 [size=16]
	Region 5: Memory at efcff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell
	Kernel modules: pata_marvell, ahci



> Bus 002 Device 005: ID 03f0:7511 Hewlett-Packard 
Bus 002 Device 004: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 002 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 002 Device 002: ID 046d:c069 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> Module                  Size  Used by
xt_limit                1382  8 
xt_tcpudp               2011  13 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
snd_usb_audio          88618  1 
snd_usbmidi_lib        17171  1 snd_usb_audio
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_emu10k1_synth       5892  0 
snd_emux_synth         34193  1 snd_emu10k1_synth
snd_seq_virmidi         4044  1 snd_emux_synth
snd_seq_midi_emul       5481  1 snd_emux_synth
iptable_nat             4414  0 
nf_nat                 15735  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10672  9 iptable_nat,nf_nat
nf_conntrack           61583  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          2771  0 
iptable_filter          2271  1 
ip_tables               9991  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               14299  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
usblp                  10481  0 
nvidia               9932176  28 
snd_emu10k1           136021  2 snd_emu10k1_synth
snd_ac97_codec        101347  1 snd_emu10k1
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            41611  0 
snd_mixer_oss          13461  1 snd_pcm_oss
snd_pcm                78086  4 snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7140  2 snd_emu10k1,snd_pcm
snd_util_mem            3266  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5668  3 snd_usb_audio,snd_emux_synth,snd_emu10k1
snd_seq_dummy           1498  0 
snd_seq_oss            30866  0 
snd_seq_midi            5101  0 
snd_rawmidi            19879  4 snd_usbmidi_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      5939  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51494  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19106  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5990  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
emu10k1_gp              1492  0 
joydev                  8708  0 
snd                    62362  25 snd_usb_audio,snd_usbmidi_lib,snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_util_mem,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
gspca_zc3xx            45189  0 
gspca_main             21199  1 gspca_zc3xx
videodev               34361  1 gspca_main
v4l1_compat            13251  1 videodev
gameport                9089  2 emu10k1_gp
asus_atk0110            9017  0 
soundcore               6620  1 snd
sbp2                   19448  0 
psmouse                63245  0 
shpchp                 28820  0 
i2c_nforce2             5199  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
pata_marvell            2140  0 
usb_storage            39425  0 
ohci1394               26950  0 
ahci                   32008  0 
ieee1394               81181  2 sbp2,ohci1394
forcedeth              49556  0 
pata_amd                8766  0 
sata_nv                19440  2 




---

### Post by lidex on 2010-05-31
> **linuxnoob40 said:**
> here ya go its long
Yes, that's why you want to use code tags(#), not quotes.
Is this a USB device? Is onboard sound disabled in bios?

---

### Post by linuxnoob40 on 2010-05-31
no im having trouble with the pulse audio it keeps crashing, and yes onboard sound is disabled in the bios im using an audigy gamer. unless for some reason that i cannot even concieve the onboard audio has been turned back on though i cannot imagine how or why

---

### Post by lidex on 2010-05-31
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.
No help? Try this:
```
sudo apt-get install --reinstall pulseaudio pulseaudio-module-x11 pavumeter paman pavucontrol libasound2 libpulse0 pulseaudio-utils libasound2-plugins
```
Logout/in.

---

### Post by linuxnoob40 on 2010-05-31
thought that had fixed it but as usual after about 4 minuts of streaming any sound it crashes

---

### Post by lidex on 2010-05-31
Try rebooting.

---

### Post by linuxnoob40 on 2010-05-31
i did like i said it works for about 4 minutes then it crashes upon reboot i see something flash across the screen that says something nforce error probing sb1 and sb2 but it flashes so quick its hard to get it all

---

### Post by linuxnoob40 on 2010-06-02
bump

---


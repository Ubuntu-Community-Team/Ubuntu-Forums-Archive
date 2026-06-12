---
title: "ALSA not detecting soundcard on reboot"
date: 2010-07-09
forum: Multimedia Software
---

### Post by Thomas Kenobi on 2010-07-09
I'm having a rather peculiar problem with sound in Ubuntu 10.04. Specifically, every time I reboot I run through a cycle of sorts:

A). Sound is working fine. Reboot
B). No sound. "aplay -l" returns "no card found". Additionally, the hibernate and suspend buttons are missing from the shutdown menu and restart acts as log out, immediately returning me to the log in screen (sudo reboot in console works). I try to fix the problem by the following commands:

```

$sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$sudo apt-get install linux-sound-base alsa-base alsa-utils
$sudo reboot

```C). After rebooting sound works normally again and I get the following:
```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```I try to use "sudo alsactl store 0" to store settings, but it doesn't always work. Nine times out of ten, when I reboot again, sound will be gone and I'll have to repeat the process.


I have a P7P55D M/B with the VIA VT1828S chipset. When everything is working I get the following results:
```

$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 14 2010 for kernel 2.6.32-23-generic (SMP).

$head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1828S

$lspci -vvnn
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8375]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 37
    Region 0: Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```
I have "linux-backports-modules-alsa-lucid-generic" installed.

Any help would be appreciated, because I'm at my wits end. I have been experiencing problems with audio since I bought this M/B, but with 9.10 things were stable and with my previous 10.04 installation bearable. Now, however, I practically can't work. I have to run the aforementioned routine every time I reboot.


Additionally, I don't if it is relevant, but the problems started after I installed the audio drivers in Windows (another royal mess, but at least now it's stable and it works). I don't know how the windows installation could have possible affected Ubuntu, but I'm mentioning it for good measure.

---

### Post by Thomas Kenobi on 2010-07-09
I just updated the BIOS, in the hopes that the issue was caused by the BIOS misreporting the soundcard to the OS, but the problem is still there.

I have also tried adding the following lines to alsa-base.conf:
```

options snd-hda-intel model=VT1828S

options snd-hda-intel probe_mask=1
or
options snd-hda-intel probe_mask=8

```

However, nothing has worked.

Does no-one have any ideas here? Any suggestions, no matter how crazy, are welcome. I'm getting pretty desperate here.

---

### Post by lidex on 2010-07-09
I think windows could affect the firmware - seen stranger things. 
I've not seen this codec anywhere. I have documented a fix for an ASUS P7P55D, but with VT2020, let's see if that works. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-digout  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by Thomas Kenobi on 2010-07-09
Thanks for the fix. So far it seems to work, though I've seen the problem disappear and then reappear before, so I'll wait 1-2 days before calling this definitely fixed. It's looking promising for the first time in six months though!

What is the model name "6stack-digout"? I had tried this setting, but with model name "VT1828S".

---

### Post by lidex on 2010-07-09
Not so much the model name, but description. It tells alsa not to use the default for the codec, instead use the pin mapping for 6 audio jacks + a digital out. A model name or quirk option has to be implemented in the code before it can be called and the one you mention is not valid.

---

### Post by ov3rcl0ck on 2010-07-09
You might not have to reinstall each time, you might just have to reload alsa, but this isn't a permanent fix. I know that every now and then Alsa fails to load properly after I login, and i just have to run this to reload it:
```

sudo alsa reload

```

---

### Post by Thomas Kenobi on 2010-07-11
@lidex: It seems the issue is well and truly gone. Many thanks for your help mate! I have been struggling with this for a long time.

@ov3rcl0ck: I didn't know that command. Thanks!__

---

### Post by afrodeity on 2010-08-08
I have similar weirdness, except it manifests only with some alsa programmes and when I start alsamixer, the sound card is not there. I have to F6 to select the soundcard, then if I select it, it comes up, but if I close and reopen alsamixer, its not there again, the same thing happens all over again. Wondering what I have to add to alsabase?


```

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug  7 2010 for kernel 2.6.32-24-generic (SMP).

head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC662 rev1


 lspci -vvnn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:0364]
	Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:0364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 8
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:1364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:2364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:3364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:4364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.5 PIC [0800]: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller [1106:5364] (prog-if 20)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes

00:00.6 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device [1106:6364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes

00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:7364]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: fdb00000-fdbfffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel modules: shpchp

00:02.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:a364] (rev 80)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:03.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:c364] (rev 80)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0f.0 IDE interface [0101]: VIA Technologies, Inc. Device [1106:5337] (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:5300]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin B routed to IRQ 21
	Region 0: I/O ports at fc00 [size=8]
	Region 1: I/O ports at f800 [size=4]
	Region 2: I/O ports at f400 [size=8]
	Region 3: I/O ports at f000 [size=4]
	Region 4: I/O ports at ec00 [size=16]
	Region 5: I/O ports at e800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at e400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3206]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 4: I/O ports at e000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3206]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 22
	Region 4: I/O ports at dc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3206]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 21
	Region 4: I/O ports at d800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3206]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin D routed to IRQ 23
	Region 4: I/O ports at d400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86) (prog-if 20)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3206]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 21
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237A PCI to ISA Bridge [1106:3337]
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3206]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e]
	Subsystem: VIA Technologies, Inc. Device [1106:337e]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 32
	Capabilities: <access denied>

00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:2200]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (750ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: I/O ports at d000 [size=256]
	Region 1: Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

00:13.0 Host bridge [0600]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a] (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

02:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 8400 GS] [10de:06e4] (rev a1)
	Subsystem: ZOTAC International (MCO) Ltd. Device [19da:4039]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 24
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidia-current, nvidiafb, nouveau

04:03.0 Communication controller [0780]: Conexant Systems, Inc. Conexant SoftK56 Data/Fax Modem [14f1:2f50] (rev 01)
	Subsystem: Conexant Systems, Inc. Device [14f1:205f]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at fdaf0000 (32-bit, non-prefetchable) [size=64K]
	Region 1: I/O ports at 9c00 [size=8]
	Capabilities: <access denied>

80:01.0 Audio device [0403]: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) [1106:3288] (rev 10)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:820f]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by afrodeity on 2010-08-08
Solved the problem. Looking at alsamixer, it showed pulseaudio as the chip and card. This pointed to the solution.

This link was helpful
[http://chrishatton.homeip.net/?p=118](http://chrishatton.homeip.net/?p=118)

But obviously I had to remove the asound.conf file setup which I had placed in the system in my attempt to fix sound issue BEFORE i upgraded alsa.

Sound is brillient right now after reboot.

I also chucked the 
 options snd-hda-intel model=6stack-digout

line into alsabase to be safe, so it could also be a factor.

---

### Post by afrodeity on 2010-08-08
Only hassle now is the lucid sound applet doesn't appear to control alsa sound volume. At least I have better sound.

---

### Post by Yellow Pasque on 2010-08-08
> **afrodeity said:**
> Only hassle now is the lucid sound applet doesn't appear to control alsa sound volume. At least I have better sound.
You can use this PPA for your issue: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by afrodeity on 2010-08-09
> **Temüjin said:**
> You can use this PPA for your issue: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

"The gnome-media/applets/settings-daemon packages are for users running without PulseAudio."

---


---
title: "No Sound And Tried Everything"
date: 2008-11-22
forum: Multimedia Software
---

### Post by WorldEvolution on 2008-11-22
When I type aplay -l I Get This
> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
When I Type This lspci -v >  RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at f400 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: fd800000-fd8fffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f019:2601
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: ata_generic, pata_acpi, pata_amd

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at dc00 [size=16]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: ata_generic, pata_acpi, sata_nv

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: sata_nv
	Kernel modules: ata_generic, pata_acpi, sata_nv

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
	Subsystem: Elitegroup Computer Systems Device 2601
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at c4000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:06.0 Communication controller: Conexant Systems, Inc. Device 2f40
	Subsystem: Conexant Systems, Inc. Device 2000
	Flags: bus master, medium devsel, latency 0, IRQ 5
	Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=8]
	Capabilities: <access denied>

01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Elitegroup Computer Systems Device 8024
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fdfff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
	Subsystem: Elitegroup Computer Systems Device 8039
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 9c00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2



Can Anyone Help Me I'm Stuck Now. I Even Tried Make Another Account Witch Didn't Work.

---

### Post by WorldEvolution on 2008-11-23
Bump.

---

### Post by zander1013 on 2008-11-23
did i miss what kind of machine you have. specifically is it an apple? i see you have a Conextant comm. device.

sometimes i have had success adding snd-powermac to the /etc/modules file on apples. for some reason alsaconf can't get this right on apples sometimes.

otherwise i would suggest running alsaconf by hand. if you still have trouble make sure you have libesd-alsa0 and gnome-audio installed.

also there is a "comprehensive" audio/sound tutorial in the sticky thread section.


peace.

---

### Post by WorldEvolution on 2008-11-23
Sorry I Forgot To Put With Comp I Have. I Have A Gateway Gt5656 Model.

---

### Post by Kevbert on 2008-11-23
What Ubuntu version are you using, could it be the 2.6.27-7 kernel ?
Use
```
uname -a 
```
to check it. It's possible that you've come across a sound bug [[COLOR="Red"]#296738[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/296738") which affects both Jaunty and Intrepid.
Have you tried looking at this [[COLOR="Red"]post[/COLOR]]("https://help.ubuntu.com/community/HdaIntelSoundHowto") ? I can't seem to find the forum post that details howto modify the alsa-base file.

---

### Post by abhilashkumar on 2008-11-23
I have the same problem. Sound stopped working on its own one day. I noticed that during shutdown ALSA was taking too much time to shut down and also startup. My sounds been off since then.

Any one know what to do?

I have an Acer 4520 Laptop.

Linux version

**Linux home-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux**

aplay output

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci Output
> 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Device cb84
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f4200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f4486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f4489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at f4487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f4489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f025:0127
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f4480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f4100000-f41fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 221
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f4484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at f4488000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at f4489c00 (32-bit, non-prefetchable) [size=256]
	Memory at f4489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f4000000-f40fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f2000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f4100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f4100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f4100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ricoh-mmc
	Kernel modules: ricoh_mmc

01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f4101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f4000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ndiswrapper
	Kernel modules: ath_pci

---

### Post by psyke83 on 2008-11-23
See here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After following the guide, check your PCM volume (there's a bug in Intrepid causing the mixer to get muted):

```
$ alsamixer -Dhw
```

---

### Post by WorldEvolution on 2008-11-23
I Am Using The 2.6.27-7. When I Added Front Mic It Give Me A Bunch Of White Noise But No Other Sound. The Post You Gave Me Is For Macs I Have A Pc.   I Went To Alsa Page And Did There Test And It Said I Didn't Need To Compile My Kernel.

---

### Post by WorldEvolution on 2008-11-24
> **psyke83 said:**
> See here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

After following the guide, check your PCM volume (there's a bug in Intrepid causing the mixer to get muted):

```
$ alsamixer -Dhw
```

Tried This Today And It Still Didn't Work.

---

### Post by RawMustard on 2008-11-24
Just install OSS4.1 from [this guide]("https://help.ubuntu.com/community/OpenSound") and all your crappy pulse-audio/alsa problems will disapear.  And your sound will never sound better :)

---

### Post by gotlinux on 2008-11-24
When I type aplay -l   I get this

aplay: device_list:215: no soundcards found...

When I type lspci -v   I get this.  It appears that my sound card is not supported.  I went to creative's support site and downloaded the tar to compile and install.  I can not get to work...  Newbie to Ubuntu.

00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8295
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f4000000-f7efffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f3fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Prefetchable memory behind bridge: 00000000f2f00000-00000000f2ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7f00000-f7ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f3fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-febfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: medium devsel, IRQ 10
	Memory at f3fff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=16]
	I/O ports at a400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
	Subsystem: Device 19f1:0719
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	Expansion ROM at f7ee0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: nvidiafb

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at f7ffc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at d800 [size=256]
	Expansion ROM at f7fc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

04:01.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 002c
	Flags: bus master, medium devsel, latency 64, IRQ 15
	I/O ports at ec00 [size=32]
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

Problem solved:  I removed the creative sound card and replaced it with the XFi sound card that came with the motherboard.  I then followed th PulseAudio guide and it works great.

---

### Post by WorldEvolution on 2008-11-25
> **RawMustard said:**
> Just install OSS4.1 from [this guide]("https://help.ubuntu.com/community/OpenSound") and all your crappy pulse-audio/alsa problems will disapear.  And your sound will never sound better :)

I Still Don't Have any sound. I went the the guide twice. Now I can't even open volume control. Anyone got anything else ? I really need sound.

---

### Post by WorldEvolution on 2008-11-25
bump still need help.

---

### Post by WorldEvolution on 2008-11-26
now when i turn front mic boost on i get this squeak noise and the test sounds work but nothing else.

---

### Post by WorldEvolution on 2008-11-27
bump.

---


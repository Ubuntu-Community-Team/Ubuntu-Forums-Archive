---
title: "no sound on my M-Audio 1010LT soundcard"
date: 2008-11-03
forum: Multimedia Software
---

### Post by Vifsorbier on 2008-11-03
Hi,
Actually I got sound on connexion screen (the tamtam sound) but once ubuntu is started there is no sound at all
I have actually two sound cards the first is intel hda with which the sound works and the second is the M1010LT
But obviously I want the sound out of my M1010LT
I read Sound Troubleshooting in help and I saw multiple sound cards can be a problem so I deactivated intel hda in BIOS but it didn't change anything
Of course I tried to unmute sound using alsamixer but : 
> stephane@Blacky-Gnuli:~$ alsamixer
No mixer elems found

stephane@Blacky-Gnuli:~$ 

I also tried several tips to get pulseaudio fixed but none gave result
I'm lost in all these things too technical for me
Please tell me what can I do

Here are the results of aplay -l and lspci -v
> stephane@Blacky-Gnuli:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: M1010LT [M Audio Delta 1010LT], périphérique 0 : ICE1712 multi [ICE1712 multi]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

> stephane@Blacky-Gnuli:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ea
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8700000-fe7fffff
	Prefetchable memory behind bridge: 00000000bfe00000-00000000dfdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fe900000-fe9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fe800000-fe8fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at d480 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at febff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	I/O ports at e080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi, ata_piix, ata_generic

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: medium devsel, IRQ 10
	Memory at 88000000 (32-bit, non-prefetchable) [disabled] [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81ec
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d400 [size=8]
	I/O ports at d080 [size=4]
	I/O ports at d000 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at c880 [size=16]
	I/O ports at c800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: pata_acpi, ata_piix, ata_generic

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 0960
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9c00 [size=128]
	[virtual] Expansion ROM at fe7e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 81e4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe8fe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at fe8e0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 81e4
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at ac00 [size=8]
	I/O ports at a880 [size=4]
	I/O ports at a800 [size=8]
	I/O ports at a480 [size=4]
	I/O ports at a400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_acpi, pata_jmicron, ata_generic


03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device 8226
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fe9a0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: atl1
	Kernel modules: atl1

05:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. Device d63b
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at bc00 [size=32]
	I/O ports at b880 [size=16]
	I/O ports at b800 [size=16]
	I/O ports at b480 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ICE1712
	Kernel modules: snd-ice1712

05:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 808a
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at b400 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

stephane@Blacky-Gnuli:~$ 


---

### Post by Vifsorbier on 2008-11-07
I uninstalled pulseaudio and installed esound and the sound is working
Though I'd like to understand what's wrong with pulseaudio, maybe it can help to find a bug

---


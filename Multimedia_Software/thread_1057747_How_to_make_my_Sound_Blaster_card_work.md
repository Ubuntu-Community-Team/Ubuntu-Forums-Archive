---
title: "How to make my Sound Blaster card work"
date: 2009-02-02
forum: Multimedia Software
---

### Post by enrico68 on 2009-02-02
My pc has two sound cards installed, one integrated into my ASUS P5K mobo, the second one a Creative Sound Blaster X-Fi Extreme Gamer. When I connect my speakers to the integrated sound card, the sound will work, if I connect the speakers to the Creative card, there's no sound, as if the operating system does not recognize it, or something. Could it be that both card can't coexist? How can I make my card work??

---

### Post by redroad55 on 2009-02-02
do you have any entry in system bios that might need to be changed..also in applications > system > administrator > hardware testing .. This will at least let you know if system recognizes your sound card .. Post back with your results and or questions ..Best to you

---

### Post by redroad55 on 2009-02-02
also this is a great guide give it a try if you have any problems with a step post back

 [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by enrico68 on 2009-02-02
> **redroad55 said:**
> do you have any entry in system bios that might need to be changed..also in applications > system > administrator > hardware testing .. This will at least let you know if system recognizes your sound card .. Post back with your results and or questions ..Best to you

Done that, last nite, it works with the integrated sound card, it does not with the Creative. I don't get it, in Windows the card works fine, not in Linux, although I just checked the Creative website, they released the source code to their drivers, so there is a Linux driver version available, I will try downloading that tonite.

---

### Post by enrico68 on 2009-02-02
> **redroad55 said:**
> also this is a great guide give it a try if you have any problems with a step post back

 [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

I'll give the guide a try tonite as well, let's see what I can accomplish...

---

### Post by redroad55 on 2009-02-02
Great .. There is a solution ..  Post back with your progress and or questions so all can learn .. Best to you

---

### Post by enrico68 on 2009-02-02
I tried with the guide posted, but my card, although recognized, is still not working, probably the drivers are not installed. I downloaded them from the creative.com website, but how do I install them?

---

### Post by enrico68 on 2009-02-02
This is what I get, if I run the command  lspci -v


enrico@enrico-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8295
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f4000000-f7dfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ac00 [size=32]
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

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f3ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Prefetchable memory behind bridge: 00000000f2f00000-00000000f2ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f7f00000-f7ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f7e00000-f7efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at a080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a480 [size=32]
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
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
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
	I/O ports at 9000 [size=8]
	I/O ports at 8c00 [size=4]
	I/O ports at 8880 [size=8]
	I/O ports at 8800 [size=4]
	I/O ports at 8480 [size=16]
	I/O ports at 8400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, pata_acpi, ata_piix

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8277
	Flags: medium devsel, IRQ 5
	Memory at f3fff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
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
	Kernel modules: ata_generic, pata_acpi, ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
	Subsystem: XFX Pine Group Inc. Device 2330
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at bc00 [size=128]
	[virtual] Expansion ROM at f7de0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 81f8
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at f7efc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at c800 [size=256]
	Expansion ROM at f7ec0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 824f
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7ffe000 (32-bit, non-prefetchable) [size=8K]
	Expansion ROM at f7fe0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 824f
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron, ata_generic, pata_acpi

05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 002c
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at ec00 [size=32]
	Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8294
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fe9ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394
As you can see, the Creative Labs SB X-Fi card is shown, but probably with no drivers...I guess, but not sure

---

### Post by enrico68 on 2009-02-02
[B]05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
Subsystem: Creative Labs Device 002c
Flags: bus master, medium devsel, latency 64, IRQ 5
I/O ports at ec00 [size=32]
Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
Capabilities: <access denied>[/B]

Here I posted the item with my Creative card, what is it saying??

---

### Post by redroad55 on 2009-02-02
I'm wondering if in the system bios you need to change a setting for system to pick up card.. check and Post back what you find..

---

### Post by enrico68 on 2009-02-02
> **redroad55 said:**
> I'm wondering if in the system bios you need to change a setting for system to pick up card.. check and Post back what you find..

See,Windows sees the card with no BIOS tweaking, I wouldn't know what to change in BIOS, I'll give it a try and come back

---

### Post by enrico68 on 2009-02-02
No, nothing to change in BIOS...

---

### Post by redroad55 on 2009-02-02
Sorry it took so long to come back have a few things going .. check in synaptic which boxes are green listed under alsa prefix .. also go to applications > system > administration > software sources >> there under third party tab is mendibuntu present in list ? while there also check updates tab and make sure unsupported (back ports) is checked .. If Medibuntu is not present go to this link and complete 
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")
Post back with the results ..Best to you

---

### Post by enrico68 on 2009-02-02
Hi Readroad, and thanks for coming back. I made the integrated sound card inactive, with no results. I don't have Medibuntu, will take a look, I am very new at this, just installed it yesterday. I will give it another try, thanks for your help

---


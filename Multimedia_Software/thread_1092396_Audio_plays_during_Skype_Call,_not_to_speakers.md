---
title: "Audio plays during Skype Call, not to speakers"
date: 2009-03-10
forum: Multimedia Software
---

### Post by WilliamBrown0000 on 2009-03-10
Hi,
    I used to be able to get Firefox to play audio to my speakers.  Now it won't.  The only time I hear audio from Firefox is when I make a Skype call.  And, there it is, playing in the background!
    I am using pulse audio in Skype, since that just seemed to work.  What information do you'll need to help?  I have included some basic output below.
    I am using on-board sound from my motherboard with a USB microphone for input.  I am running 8.10 on my desktop.
    Thanks very much in advance.

     Bill

+++++++++++++++++++++++++++++++++++++++
bbrown@parvathi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CODEC [USB audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


bbrown@parvathi:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 82d3
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fe9fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9fff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at a000 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9880 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9480 [size=16]
	I/O ports at 9400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: medium devsel, IRQ 15
	Memory at f9fff400 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82d4
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at b000 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at a880 [size=8]
	I/O ports at a800 [size=4]
	I/O ports at a480 [size=16]
	I/O ports at a400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
	Subsystem: eVga.com. Corp. Device c975
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device 8304
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at feac0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at dc00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ATL1E
	Kernel modules: atl1e

03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82e0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=16]
	Memory at febffc00 (32-bit, non-prefetchable) [size=512]
	Capabilities: <access denied>
	Kernel driver in use: pata_marvell
	Kernel modules: pata_marvell

---

### Post by WilliamBrown0000 on 2009-03-10
Hi,
    Just to be clear, I play audio in Firefox and cannot hear the the audio via my speakers.  I start-up SKYPE and make a call.  The person on the call can hear me, I can hear them, and only the person on the call can hear my browser playing audio.  I can't hear my browser at all.
    Help!

           Bill

---


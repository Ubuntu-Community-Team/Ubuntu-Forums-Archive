---
title: "Integrated sound card not working"
date: 2009-02-21
forum: Multimedia Software
---

### Post by UberNubeR-2k on 2009-02-21
Hello:

I have tried many guides, but none seem to have helped me out. I have an integrated sound card and it seems to be detected but not working.

If I type "lspci -v" in Terminal this is what shows:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Subsystem: Dell Device 0080
	Flags: bus master, medium devsel, latency 64
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: e0000000-efffffff
	Kernel modules: shpchp

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at dce0 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
	Flags: medium devsel, IRQ 9
	Kernel modules: i2c-piix4

00:0e.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
	Subsystem: Aztech System Ltd Device 4003
	Flags: medium devsel, IRQ 17
	Memory at fe000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
	Subsystem: Dell Device 0080
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at dc00 [size=128]
	Memory at fe010000 (32-bit, non-prefetchable) [size=128]
	Expansion ROM at f9000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

00:13.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
	Flags: bus master, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-fbffffff
	Prefetchable memory behind bridge: 00000000f5000000-00000000f5ffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
	Subsystem: nVidia Corporation Device 0091
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at e0000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, rivafb

02:0a.0 SCSI storage controller: Adaptec AHA-2940U2/U2W / 7890/7891
	Subsystem: Dell Device 0080
	Flags: bus master, medium devsel, latency 64, IRQ 18
	BIST result: 00
	I/O ports at ec00 [disabled] [size=256]
	Memory at fafff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: aic7xxx
	Kernel modules: aic7xxx

02:0e.0 SCSI storage controller: Adaptec AIC-7880U (rev 01)
	Subsystem: Adaptec Device 7880
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at e800 [disabled] [size=256]
	Memory at faffe000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at f5000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: aic7xxx
	Kernel modules: aic7xxx
```
look at the Rockwell International card, it's the sound one.

So, what should I do?

---

### Post by UberNubeR-2k on 2009-02-21
anybody?

---

### Post by wolfen69 on 2009-02-21
the rockwell is your modem, and not a sound card. check your BIOS to see if your onboard sound is enabled. then do
```
lspci
```and post here.

---

### Post by UberNubeR-2k on 2009-02-21
OH, hehe.



I checked my BIOS and the sound card is on.

lspci:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 Serial controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone]
00:13.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:0a.0 SCSI storage controller: Adaptec AHA-2940U2/U2W / 7890/7891
02:0e.0 SCSI storage controller: Adaptec AIC-7880U (rev 01)

```

---


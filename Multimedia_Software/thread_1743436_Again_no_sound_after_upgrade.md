---
title: "Again no sound after upgrade"
date: 2011-04-29
forum: Multimedia Software
---

### Post by smart734 on 2011-04-29
Hello, i have this problem from version 10.04, after upgrade, there isn't sound. I solve it with reinstall linux, but i don't want to do it again. :( I found to install padevchooser, but nothing write if i run it in terminal. I found this command 
cat /proc/asound/card0/codec#* | grep Codec

cat: /proc/asound/card0/codec#*: Adresá&#345; nebo soubor neexistuje
"Adresá&#345; nebo soubor neexistuje"-It is doesn't exist

Can anyone help me. This is command lspci -v

```
martin@kluci:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 8178
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: dc000000-ddffffff
	Prefetchable memory behind bridge: 00000000de000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5LD2-VM Mainboard (Realtek ALC 882 codec)
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at dbef8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: c0000000-c01fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dbf00000-dbffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 8000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 8400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 8800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at dbeffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 2601
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
	I/O ports at a800 [size=8]
	I/O ports at a400 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
	Flags: medium devsel, IRQ 4
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. P5B
	Flags: bus master, fast devsel, latency 0, IRQ 43
	I/O ports at c800 [size=256]
	Memory at dbfff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at dbfe0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 240] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Micro-Star International Co., Ltd. Device 8041
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e800 [size=128]
	[virtual] Expansion ROM at ddf00000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

04:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Device 8041
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at ddffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel


```
I'm not using HDMI, only analog. 
And if i go to sound preferences, there isn't hardware.
I'm beginner.
Thanks for help. :)

---

### Post by KegHead on 2011-04-29
Hi!

It shows no hardware to configure?

---

### Post by smart734 on 2011-04-30
Yes, but i found solution. I deleted in /etc/modprobe.d file blacklist-noALSA.conf Thanks :)

---


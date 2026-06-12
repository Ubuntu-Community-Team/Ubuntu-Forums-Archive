---
title: "WIFI Problems, HP Pavilion Desktop / best USB wifi"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by tomreid on 2011-09-10
Hi

I bought an HP Pavilion desktop around May of 2009 when I lived in California. Accessed the home network in the US by wifi.

I brought it back home to the UK, swapped it's voltage round at the back as the HP support people told me to. It seemed to work fine. But I only used it on ethernet at our first new house in the uk.

Now we have moved house, I put it in our new home office which is well away from an ethernet port. 

No sign of any working wifi. I'm using wifi to write this message on a little Dell netbook in the attic, so I know I have a signal here.

From the output of lspc -v below, it looks as if the wifi card has a hardware fault as I can't see any mention of a card, can someone help me confirm this?

As I'm a very busy father of one (soon to be two) i really don't have the time to do the technical stuff i used to, so if the wifi card is broken I was looking for the easiest fix, which I imagined was to plug in a usb wifi device. 

Can someone help me with a recommendation of a compatible device?

One that would  just plug and play in 11.04?

cheers

	tom@tom-Desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b480 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f7efec00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at f7ef4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0000000-f01fffff
	Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000f6f00000-00000000f6ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at b800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at b880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f7eff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f7f00000-f7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c080 [size=32]
	Memory at f7eff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: medium devsel, IRQ 10
	Memory at f7effc00 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f7fff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 2a6f
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f6ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
	Subsystem: Creative Labs Device 0045
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f9ff0000 (64-bit, non-prefetchable) [size=64K]
	Memory at f9c00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: SB-XFi
	Kernel modules: snd-ctxfi

05:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9300 GE] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Device 1b0a:9004
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-173, nvidia-current, nouveau, nvidiafb

tom@tom-Desktop:~$

---

### Post by tomreid on 2011-09-16
anyone?

---

### Post by ibutho on 2011-09-16
If this is onboard wifi, have you double checked that wifi is on? On my HP laptop, I have a little switch that turns on/off wireless and bluetooth.

---

### Post by praseodym on 2011-09-16
Maybe its an internal USB-device? Please show:

```
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---


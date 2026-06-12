---
title: "[SOLVED] Can I use my TV card with Ubuntu?"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by Damien Kane on 2008-04-20
Hi all,

I think I read somewhere that you can watch TV in Linux. I've got a Hauppauge WinTV HVR-1200 hybrid and was wondering what software if any, I can use with it? Like, with Windows, it's all pre-installed for me with Windows Media Centre and works with a remote control. Is there some sort of Ubuntu-equivalent? I'm using the 7.10 version at present and will move up to the next version when released.

Many thanks for your time. I appreciate it.

---

### Post by xc3RnbFO8P on 2008-04-20
In Terminal:
> lspci -v
Show the ouput.

---

### Post by Damien Kane on 2008-04-20
Here's the output:

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at b400 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at b480 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f9cfec00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f9cf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f9e00000-f9ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: feb00000-febfffff
        Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at b880 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at bc00 [size=32]
        Capabilities: <access denied>

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f9cff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f9d00000-f9dfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at c880 [size=8]
        I/O ports at c800 [size=4]
        I/O ports at c480 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c080 [size=32]
        Memory at f9cff000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: medium devsel, IRQ 10
        Memory at f9cffc00 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0400 [size=32]

01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9dff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 2a6f
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at e800 [size=256]
        Memory at febff000 (64-bit, non-prefetchable) [size=4K]
        Memory at f8ff0000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)
        Subsystem: Hauppauge computer works Inc. Unknown device 71d3
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f9e00000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 034e
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        Expansion ROM at feae0000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by xc3RnbFO8P on 2008-04-20
It is not supported yet.

---

### Post by Damien Kane on 2008-04-21
No worries. Thanks for looking at the prob.

---


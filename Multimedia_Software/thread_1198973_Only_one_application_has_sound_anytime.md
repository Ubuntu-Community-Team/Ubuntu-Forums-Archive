---
title: "Only one application has sound anytime"
date: 2009-06-28
forum: Multimedia Software
---

### Post by afeasfaerw23231233 on 2009-06-28
For example, I was listening to music by VLC player. Then I started firefox and visited youtube, but youtube didn't have any sound. I had to switch off both applications and then started firefox again. This time I could hear sound from youtube. But if I started VLC without closing firefox, VLC would have no sound. 

I am running ubuntu 8.04 64-bit. 

aplay -l ```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
lspci -v
```


00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8178
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dc000000-dfffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 817f
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at dbef8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dbf00000-dbffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 8000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 8400 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 8800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 9000 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at dbeffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Unknown device 2601
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
	I/O ports at a800 [size=8]
	I/O ports at a400 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9800 [size=4]
	I/O ports at 9400 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8179
	Flags: medium devsel, IRQ 6
	I/O ports at 0400 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81aa
	Flags: bus master, fast devsel, latency 0, IRQ 508
	I/O ports at c800 [size=256]
	Memory at dbfff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at dbfe0000 [disabled] [size=64K]
	Capabilities: <access denied>

04:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Unknown device 0523
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at e800 [size=128]
	[virtual] Expansion ROM at defe0000 [disabled] [size=128K]
	Capabilities: <access denied>


```

Thanks in advance!

P.S. System > Preference > Sound > Enable Software sound mixing is ticked

---

### Post by Patsoe on 2009-06-28
I've had the same problems here now and then... The best solution seems to be upgrading to a newer version: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---


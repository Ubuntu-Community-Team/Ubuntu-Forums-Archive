---
title: "no sound on Lenovo Y410"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by nipponzen on 2008-03-18
When I first installed Ubuntu 7.10, the sound worked when I logged on... now it doesn't even make a beep.
I have installed all updates and tried reinstalling ALSA and packages but still no sound...  at least it is recognizing my drivers:
Here the lspci
```
naoki@unistat-pc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

**and this is lspci -v**
```
naoki@unistat-pc:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
        Subsystem: Lenovo Unknown device 383c
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 383e
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8000000 (64-bit, non-prefetchable) [size=1M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
        Subsystem: Lenovo Unknown device 383e
        Flags: bus master, fast devsel, latency 0
        Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3846
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3847
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 3849
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8504000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Unknown device 384e
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f8300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c0000000-c3ffffff
        Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f0000000-f3ffffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: b8000000-bbffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c9ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3843
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3844
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Lenovo Unknown device 3845
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Lenovo Unknown device 3848
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8504400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
        Memory behind bridge: f8200000-f82fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Lenovo Unknown device 3840
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Lenovo Unknown device 3841
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18e0 [size=16]
        I/O ports at 18d0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Lenovo Unknown device 3842
        Flags: medium devsel, IRQ 10
        Memory at 88000000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1000
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
        Subsystem: Lenovo Unknown device 3861
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at b8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Lenovo Unknown device 3829
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Lenovo Unknown device 382a
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at f8200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Lenovo Unknown device 382b
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Lenovo Unknown device 382c
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Lenovo Unknown device 382d
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at f8201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```
please help

---

### Post by nipponzen on 2008-03-18
*fixed it.

---

### Post by idx on 2008-04-01
How?

I have the same lappy. Still struggling :confused:

---

### Post by xc3RnbFO8P on 2008-04-01
What have you done so far?

---

### Post by idx on 2008-04-02
I have tried various methods suggested in the forums. But i have been avoiding compiling the kernel.

I have got sound working in PCLinuxOS just by entering "fujitsu" in the Model field of the Driver Module Configuration.

In all the methods i have tried i have mentioned "lenovo"

I guess the proper option is "fujitsu" NOT "lenovo".  

"options snd-hda-intel index=0 model=fujitsu"

Will not try it on gusty now. Will wait for Hardy to see if sound works without any intervention.

---

### Post by xc3RnbFO8P on 2008-04-02
It should be enough to install alsa 1.0.16 with out the "fujitsu" or "lenovo".

---

### Post by idx on 2008-04-03
PCLinuxOS already has 1.0.16. But still had the problem. This is a major problem across all distros mostly with intel.

---

### Post by xc3RnbFO8P on 2008-04-03
Try to install** linux backports modules generic**, (before making a fresh install of Hardy Heron)

---


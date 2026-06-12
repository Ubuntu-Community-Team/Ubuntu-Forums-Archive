---
title: "SB Audigy Live - no sounds"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by theclifster on 2007-11-04
I have read many online forum comments with people not being able to get SB Audigy LS to give any sounds under various Ubuntu releases. I also have this problem. I have installed ubuntu 64 and now 32 bit and have never managed to even get one tweet out of the speakers on 7.04 or 7.10. The sounds card works fine under various Windows releases.

I think the issue is an imcompatiblity between OSS and Alsa...but I am new to Linux and I haven't got the skills to prove this. Let alone th confidence to try to remove one or the other without assistance.

Other than trying to uncompile the Ubuntu Kernel and remove OSS...does anyone have any suggestions? 

I include the following systems info in case this is useful.

//////////////////////////////////////////////
modinfo soundcore
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:
vermagic:       2.6.22-14-generic SMP mod_unload 586
//////////////////////////////////////////////

more /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      AudigyLS [Unknown] at 0x8000 irq 22
 1 [U0xd8c0x0c     ]: USB-Audio - USB Device 0xd8c:0x0c
                      USB Device 0xd8c:0x0c at usb-0000:00:02.0-9, full speed
//////////////////////////////////////////////

ls /proc/asound/ -l
total 0
lrwxrwxrwx  1 root root 5 2007-11-04 14:07 CA0106 -> card0
dr-xr-xr-x 10 root root 0 2007-11-04 14:07 card0
dr-xr-xr-x  4 root root 0 2007-11-04 14:07 card1
-r--r--r--  1 root root 0 2007-11-04 14:07 cards
-r--r--r--  1 root root 0 2007-11-04 14:07 devices
-r--r--r--  1 root root 0 2007-11-04 14:07 hwdep
-r--r--r--  1 root root 0 2007-11-04 14:07 modules
dr-xr-xr-x  2 root root 0 2007-11-04 14:07 oss
-r--r--r--  1 root root 0 2007-11-04 14:07 pcm
dr-xr-xr-x  2 root root 0 2007-11-04 14:07 seq
-r--r--r--  1 root root 0 2007-11-04 14:07 timers
lrwxrwxrwx  1 root root 5 2007-11-04 14:07 U0xd8c0x0c -> card1
-r--r--r--  1 root root 0 2007-11-04 14:07 version
//////////////////////////////////////////////
more /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14 emulation code)
Kernel: Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
AudigyLS [Unknown] at 0x8000 irq 22
USB Device 0xd8c:0x0c at usb-0000:00:02.0-9, full speed

Audio devices:
0: CA0106 (DUPLEX)
1: USB Audio (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: CA0106 MPU-401 (UART)

Timers:
31: system timer
//////////////////////////////////////////////




00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
05:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]
05:00.1 Display controller: ATI Technologies Inc Unknown device 7264


00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at e000 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f2102000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at f2104000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        Memory at f2100000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at dc00 [size=16]
        Memory at f2101000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: f2000000-f20fffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Giga-byte Technology GA-K8N Ultra-9 Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f2103000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e400 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f0000000-f1ffffff
        Prefetchable memory behind bridge: 0000000048000000-00000000480fffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0000000-efffffff
        Prefetchable memory behind bridge: 0000000048100000-00000000481fffff
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 1013
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at 8000 [size=32]
        Capabilities: <access denied>

01:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Belkin Unknown device 700e
        Flags: bus master, slow devsel, latency 32, IRQ 21
        Memory at f2000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
        Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at f1000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 9000 [size=256]
        [virtual] Expansion ROM at 48000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e1000000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at a000 [size=256]
        [virtual] Expansion ROM at 48100000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.1 Display controller: ATI Technologies Inc Unknown device 7264
        Subsystem: ATI Technologies Inc Unknown device 0b13
        Flags: bus master, fast devsel, latency 0
        Memory at e1010000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

---


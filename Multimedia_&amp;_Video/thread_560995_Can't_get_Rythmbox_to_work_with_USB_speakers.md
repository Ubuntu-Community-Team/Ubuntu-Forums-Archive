---
title: "Can't get Rythmbox to work with USB speakers"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by jasnils on 2007-09-27
**Please do tell**, if somebody can help me get sound in Rythmbox Music Player.:confused:

I have a Ubuntu feisty fawn installed on a Sony Vaio Multimedia machine:

Logitech USB Speakers:

do work with Skype, Xmms, Ekiga softphone
do not work with Rythmbox music player, firefox, opera

The speakers do interact with Ubuntu and when I push the right buttons on one of the speakers, I see signals on the screen for:

increase volume 
decrease volume
mute
next song
previous song

**Just no sound**

**Sound preferences:** Default mixer tracks: Logitech USB Speakers (Alsa Mixer)
For all devices I have tried changing from: automatic, usb audio, alc880 analog, alsa, esd, oss

for all test buttons, I only get a horn when on USB audio.

**Sound cards:**

@VAIO-UBUNTU:~**$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Speaker [Logitech USB Speaker], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

@VAIO-UBUNTU:~**$ lspci -v**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
        Subsystem: Sony Corporation Unknown device 819b
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f0000000-fbefffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 81a0
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at a480 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at a800 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at a880 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ac00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at dfffbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: fbf00000-fbffffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000deffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Sony Corporation Unknown device 819d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]

00:1f.2 RAID bus controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 819f
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at a400 [size=8]
        I/O ports at a080 [size=4]
        I/O ports at a000 [size=8]
        I/O ports at 9c00 [size=4]
        I/O ports at 9880 [size=16]
        Memory at dfffb800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Sony Corporation Unknown device 819d
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] (prog-if 00 [VGA])
        Subsystem: Sony Corporation Unknown device 0005
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b000 [size=256]
        Memory at f0000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fbee0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:03.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 811e
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

03:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Sony Corporation Unknown device 813d
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

03:06.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
        Subsystem: Sony Corporation Unknown device 81a2
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
        Memory at fbfc0000 (32-bit, non-prefetchable) [size=128K]
        Memory at fbfa0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at dc00 [size=64]
        Expansion ROM at dc000000 [disabled] [size=128K]
        Capabilities: <access denied>

03:07.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
        Subsystem: Sony Corporation Unknown device 8139
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at fbf00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

---


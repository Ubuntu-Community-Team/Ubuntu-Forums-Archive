---
title: "D-link DWL-G510 marvell Chipset not recognized"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by yakkob on 2006-05-07
D-link DWL-G510 with marvell marvell W8300 Chipset

Last night I had it up! I really did! My laptop running windows xp picked up the ad-hoc network I setup and it seemed like things were going to work, I was too tired to figure out how to setup the internet connection sharing so I shut everything down and went to bed.  Hoping to continue in the morning.

When I woke up this morning Ubuntu didn't even recognize the card as Marvell in Device manager anymore, and there is nothing when I try everything with ndiswrapper..  
I am not sure what to do anymore.

Here's what I am dealing with.

> david@Optimus:~$ lspci -v
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
        Subsystem: Asustek Computer, Inc.: Unknown device 8081
        Flags: bus master, medium devsel, latency 32
        Memory at f0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ef000000-efffffff
        Prefetchable memory behind bridge: f7700000-febfffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
        Flags: medium devsel
        I/O ports at e600 [size=32]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Asustek Computer, Inc.: Unknown device 807a
        Flags: bus master, medium devsel, latency 128, IRQ 16
        I/O ports at b400 [size=16]

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ee000000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at ed800000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at ed000000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Asustek Computer, Inc.: Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 23
        Memory at ec800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
        Subsystem: Asustek Computer, Inc.: Unknown device 80a7
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 9800 [size=256]
        Memory at ec000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at f76c0000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at 9400 [size=32]
        Capabilities: <available only to root>

0000:00:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at 9000 [size=8]
        Capabilities: <available only to root>

0000:00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at eb800000 (32-bit, non-prefetchable) [size=2K]
        Memory at eb000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 00 [Generic])
        Subsystem: PCTel Inc: Unknown device 0001
        Flags: stepping, medium devsel, IRQ 17
        I/O ports at 8800 [size=64]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 8783
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at ef000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Memory at f7800000 (32-bit, prefetchable) [size=512K]
        Expansion ROM at f77e0000 [disabled] [size=128K]
        Capabilities: <available only to root>


I installed the card myself.  Yesturday.
I have googled everything I could think of. I have always found my questions answered through forums and such when I have dealt with other distributions and problems that have come up with ubuntu. Ubuntu is by far the best I have dealt with.. But this one has me stumped...

Thanks!

---

### Post by yakkob on 2006-05-07
Hey forget it.
Call me impatient but I just pulled all my cards out shuffled them like an old poker player and snapped em all back in wherever they landed.  
Booted this ugly box up and, and what do you know up she came.  Marvell card right there. I don't know what I did but it worked...

No need for any help.  now I am off to learn how to share an internet connection wirelessly.

---


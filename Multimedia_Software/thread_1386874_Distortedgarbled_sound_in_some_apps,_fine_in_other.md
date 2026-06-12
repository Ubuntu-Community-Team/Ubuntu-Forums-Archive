---
title: "Distorted/garbled sound in some apps, fine in others."
date: 2010-01-21
forum: Multimedia Software
---

### Post by knurledflanges on 2010-01-21
Hello, I just installed Ubuntu 9.10 and also have xubuntu-desktop installed. The problems I'm experiencing appear the same in both desktops.

Sound from things like Rhythmbox and all the bundled Ubuntu apps I've tried was fine out of the box. (This install does have the quirk that the volume is set to 0 every time I start up, which wasn't the case in my previous wubi install.)

However, all sound in several games I've tried is choppy, mixed up, and hissy. It sounds  like random garble is coming out when the game is telling the system to play a sound. So far these include Teeworlds and SuperTuxKart. They behave in the same manner. Several other games (example SDL-Ball) are fine.

Doing "aplay -l" gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Doing 'lspci -v' gives:

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
    Subsystem: ASRock Incorporation Device 3156
    Flags: bus master, 66MHz, medium devsel, latency 8
    Memory at e0000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: dbe00000-dfefffff
    Prefetchable memory behind bridge: bbd00000-dbcfffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
    Subsystem: Linksys Device 0032
    Flags: bus master, slow devsel, latency 32, IRQ 17
    Memory at dfffe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: rt2500pci
    Kernel modules: rt2500pci

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at e800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
    Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at ec00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20)
    Subsystem: VIA Technologies, Inc. USB 2.0
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at dfffdf00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
    Subsystem: ASRock Incorporation Device 3177
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation Device 0571
    Flags: bus master, medium devsel, latency 32, IRQ 255
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
    Subsystem: VIA Technologies, Inc. Device 4161
    Flags: medium devsel, IRQ 22
    I/O ports at e000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
    Subsystem: ASRock Incorporation Device 3065
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at dc00 [size=256]
    Memory at dfffde00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
    Subsystem: Giga-byte Technology Device 343c
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at dfee0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

```Thanks!

---

### Post by mörgæs on 2010-01-21
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by knurledflanges on 2010-01-21
> **mörgæs said:**
> [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Thanks so much, I found my answer in [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#No%20sound%20or%20stuttering%20sound%20in%20SDL-based%20games](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#No%20sound%20or%20stuttering%20sound%20in%20SDL-based%20games) . Installed  [libsdl1.2debian-pulseaudio]("apt://libsdl1.2debian-pulseaudio") in synaptic and everything works.:D

---


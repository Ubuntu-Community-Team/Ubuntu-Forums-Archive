---
title: "[SOLVED] 8.0.4 -- tried to install Nvidia but now no sound!"
date: 2008-10-06
forum: Multimedia Software
---

### Post by shadowfirebird on 2008-10-06
Hi, 

Today I have no sound.  Yesterday it worked fine (ALSA).

Last night?  Right.  Last night I ran EnvyNG to try an get my graphics card working, which failed.  Which is another story.  Right now I'm concentrating on getting the sound back. 

I've ran Envy in deinstall mode, then deinstalled another package it missed, and rebooted. Nothing.  I'm afraid I'm out of my depth here.  

Some outputs:

```
andy@Blake:~$ aplay -l
aplay: device_list:205: no soundcards found...

```

not a good sign!

```
andy@Blake:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Subsystem: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 Sout
h] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e4000000-e6ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Cont
roller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Pinnacle Systems Inc. Unknown device 000e
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at e7004000 (32-bit, non-prefetchable) [size=2K]
        Memory at e7000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (r
ev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Giga-byte Technology GA-7VM400AM(F) Motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 9000 [size=8]
        I/O ports at 9400 [size=4]
        I/O ports at 9800 [size=8]
        I/O ports at 9c00 [size=4]
        I/O ports at a000 [size=16]
        I/O ports at a400 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/
C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at a800 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at ac00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at b000 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at b400 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
 (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHC
I])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at e7005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T89
0 South]
        Subsystem: Giga-byte Technology GA-7VT600 Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A
C97 Audio Controller (rev 60)
        Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
        Flags: medium devsel, IRQ 11
        I/O ports at bc00 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 19
        I/O ports at c000 [size=256]
        Memory at e7006000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
nsport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address 
Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con
troller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella
neous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GT (rev a2) (
prog-if 00 [VGA controller])
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e5000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e6000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

...so the card hasn't been stolen in the night.  

"sudo modprobe snd-" and then hitting tab ... gets me nothing.  No sound modules running, I guess.

I'd be really greatful for any suggestions at this point.  Ta.

UPDATE: I've just nerved myself to try:
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop fast-user-switch-applet
```
"no apparent effect".

UPDATE 2: 
1) I have no directory /proc/asound
2) I had a look in /etc/modprobe.d/alsa-base and noticed some modprobe lines:
```
andy@Blake:~$ sudo modprobe snd-card-0
FATAL: Module snd_card_0 not found.
```

---

### Post by shadowfirebird on 2008-10-07
This is really doing my head in.  I'd really welcome any comments, even "ooh, that looks nasty"...  ta.

---

### Post by shadowfirebird on 2008-10-07
Sorted -- see [here]("http://ubuntuforums.org/showthread.php?t=940724")

---


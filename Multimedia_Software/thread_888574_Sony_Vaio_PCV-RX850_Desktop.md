---
title: "Sony Vaio PCV-RX850 Desktop"
date: 2008-08-13
forum: Multimedia Software
---

### Post by froman2686 on 2008-08-13
I've downloaded and installed Kubuntu Hardy with no issues. Everything's installed, autodetected, etc etc...except I'm getting ZERO sound output. I've been trying to get either the 2.1 audio out or the built in optical audio, but I can't coax a single note from either.

aplay -l
> coleco-32@Coleco-32:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v
> coleco-32@Coleco-32:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8079
        Flags: bus master, medium devsel, latency 32
        Memory at ec000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: eb800000-ebffffff
        Prefetchable memory behind bridge: f0000000-febfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at e600 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: Sony Corporation Unknown device 8133
        Flags: bus master, medium devsel, latency 32, IRQ 17
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at a400 [size=16]

00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Sony Corporation Unknown device 8128
        Flags: medium devsel, IRQ 16
        I/O ports at a000 [size=256]
        I/O ports at 9800 [size=128]
        Capabilities: <access denied>

[B]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Sony Corporation Unknown device 8127
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at 9400 [size=256]
        I/O ports at 9000 [size=128]
        Capabilities: <access denied>[/B]

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 8133
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at eb000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 8133
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at ea800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 8133
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at ea000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: Sony Corporation Unknown device 8133
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at e9800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Sony Corporation Unknown device 80ea
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 8800 [size=256]
        Memory at e9000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:13.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) (prog-if 10 [OHCI])
        Subsystem: Sony Corporation Unknown device 811e
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at e8800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter (prog-if 00 [VGA controller])
        Subsystem: Sony Corporation Unknown device 811c
        Flags: 66MHz, medium devsel, IRQ 10
        BIST result: 00
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at eb800000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d800 [size=128]
        Capabilities: <access denied>


KMix reports that I have a SiS SI7012.

I've downloaded the latest alsa packages, and all of my volume settings are way the hell up, but still I get nothing. Anyone have any insights as to why this might be? Thanks!

---

### Post by null byte on 2008-08-13
Try killing pulseaudio? (pkill pulseaudio)

---

### Post by froman2686 on 2008-08-13
Doesn't seem to have any effect...

---

### Post by null byte on 2008-08-13
System - Prefences - Sound

Is everything set to ALSA?

---

### Post by froman2686 on 2008-08-14
yep. sound settings, amarok settings, you name it. Still nothing.

---

### Post by null byte on 2008-08-14
Have you tried:
```
sudo apt-get install alsamixergui
```
then starting it, and adjust the stuff there?

---

### Post by froman2686 on 2008-08-14
Nothing jumps out as incorrect. I set everything all the way to full, to be sure. 

Is there any other information I could get that might help? I'm fairly certain this isn't related to volume...something else has to be wrong, somewhere. I'm at a loss as to what that could be, though.

---

### Post by null byte on 2008-08-15
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by froman2686 on 2008-08-15
Guide was incredibly informative and provided a wealth of things to try. After having completed all of it (up to and including building my own drivers from source) I am still without sound. I matched up my sound device with the snd_intel8x0 driver from the Alsa page, built it, modprobed, nothing. Rebooted, nothing. 

I think maybe I might just go buy a dedicated sound card. Idk what the hell is going on here, but this one seems to be resisting every attempt to make it work properly.

---


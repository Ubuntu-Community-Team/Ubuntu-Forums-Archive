---
title: "Noob and No Sound"
date: 2008-09-05
forum: Multimedia Software
---

### Post by ADSY9111 on 2008-09-05
Ok ive recently converted to linux (just now) and i have no sound.

How do i find out what my sound card is so i can install the drivers.

---

### Post by ronnielsen1 on 2008-09-05
Go to Accessories > Terminal

Type in ***lspci*** and post the output in this forum.

---

### Post by ADSY9111 on 2008-09-05
> **ronnielsen1 said:**
> Go to Accessories > Terminal

Type in ***lspci*** and post the output in this forum.

Thanks for the fast reply...

```
user@user-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
user@user-desktop:~$ 

```

---

### Post by Crafty Kisses on 2008-09-05
I'd also like to see > lspci -v

---

### Post by ADSY9111 on 2008-09-05
> **Codename said:**
> I'd also like to see > lspci -v

```
user@user-desktop:~$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
        Subsystem: ASRock Incorporation Unknown device 0741
        Flags: bus master, medium devsel, latency 0
        Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: cfd00000-cfefffff
        Prefetchable memory behind bridge: bfa00000-cfbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 0c00 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ASRock Incorporation Unknown device 5513
        Flags: bus master, medium devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at cfff9000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at cfffa000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 7002
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASRock Incorporation Unknown device 0900
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at d800 [size=256]
        Memory at cfff8000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at dc00 [size=8]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: ASRock Incorporation Unknown device 6331
        Flags: 66MHz, medium devsel, IRQ 11
        BIST result: 00
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        Memory at cfee0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at bc00 [size=128]
        Capabilities: <access denied>

```

---

### Post by Crafty Kisses on 2008-09-05
Have you checked the **Hardware Drivers** option to see if it's listed there?

---

### Post by ADSY9111 on 2008-09-05
> **Codename said:**
> Have you checked the **Hardware Drivers** option to see if it's listed there?

How do i do that?

---

### Post by tspan on 2008-09-06
> How do i do that?

System -> Administration -> Hardware Drivers

Did you read [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")?

---


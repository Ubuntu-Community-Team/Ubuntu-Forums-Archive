---
title: "NVidia GeForce MX 4000"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Reggaeton King on 2006-09-03
I just brought my first PCI Graphics Card. I installed it on my PC. I dual-boot Ubuntu 6.06 and Windows XP. It was great on Windows XP but Ubuntu won't even load up when I try it. What should I do?

---

### Post by tseliot on 2006-09-03
1) What's your integrated card?

2) Can you post the output of this command?
```
lspci -v
```

---

### Post by Reggaeton King on 2006-09-03
Output:
[PHP]
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host ( rev 03)
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ec000000-ec0fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media I O] (rev 25)
        Flags: bus master, medium devsel, latency 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 10c0 [size=32]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if  80 [Master])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 128, IRQ 169
        I/O ports at 4000 [size=16]
        Capabilities: <available only to root>

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at e000 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <available only to root>

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at ec124000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at ec125000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller  (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ec122000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 91)
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at e800 [size=256]
        Memory at ec123000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:08.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)
        Subsystem: Linksys Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 201
        Memory at ec120000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741 /760/761 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: VGA palette snoop, 66MHz, medium devsel, IRQ 5
        BIST result: 00
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at ec000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=128]
        Capabilities: <available only to root>

[/PHP]

---

### Post by tseliot on 2006-09-04
> **Reggaeton King said:**
> Output:
[PHP]
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host ( rev 03)
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: ec000000-ec0fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media I O] (rev 25)
        Flags: bus master, medium devsel, latency 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 10c0 [size=32]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if  80 [Master])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 128, IRQ 169
        I/O ports at 4000 [size=16]
        Capabilities: <available only to root>

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at e000 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: <available only to root>

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at ec124000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at ec125000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller  (prog-if 20 [EHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at ec122000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 91)
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at e800 [size=256]
        Memory at ec123000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:08.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)
        Subsystem: Linksys Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 32, IRQ 201
        Memory at ec120000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741 /760/761 PCI/AGP VGA Display Adapter (prog-if 00 [VGA])
        Subsystem: Foxconn International, Inc.: Unknown device 0c4d
        Flags: VGA palette snoop, 66MHz, medium devsel, IRQ 5
        BIST result: 00
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at ec000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=128]
        Capabilities: <available only to root>

[/PHP]
Ok, you need to follow this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

But you have to replace "intel_agp" with "sis_agp" in point 3

And there's no need to use Option "NvAGP" "1" in point 4

The rest of the guide is fine.

---


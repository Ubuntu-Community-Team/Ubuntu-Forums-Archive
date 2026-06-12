---
title: "Ubuntu 7.10 gutsy no sound and no visual effects"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by Northern Pilgrim on 2007-11-13
Hi I'm very new to Ubuntu and trying to give it my best but for the last two weeks I've been trying to install it on my older computer an get no sound or special graphics. Here is my lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:05.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF

I really hope someone can help me to free myself of Windows

Discouraged Northern Pilgrim

---

### Post by Northern Pilgrim on 2007-11-26
Hi again, I solved my graphics issue by purchasing a new GeForce FX5200 but I just bought the audio card and would really appreciate a helping hand. So here is my problem, my audio card is Audigy SE and my pci listing sees it as Audigy LS and it is not detected.
i.e. 
me@Northern-Pilgrim:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
        Flags: bus master, medium devsel, latency 120
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at eddff000 (32-bit, prefetchable) [size=4K]
        I/O ports at da00 [disabled] [size=4]
        Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 120
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ede00000-efefffff
        Prefetchable memory behind bridge: d5c00000-e5cfffff

00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
        Flags: medium devsel

00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 16, IRQ 5
        Memory at efffe000 (32-bit, non-prefetchable) [size=4K]

00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Accton Technology Corporation Unknown device ec02
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at dc00 [size=256]
        Memory at effffc00 (32-bit, non-prefetchable) [size=1K]
        Expansion ROM at effc0000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: medium devsel, IRQ 10
        I/O ports at de00 [size=32]
        Capabilities: <access denied>

01:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology Unknown device 3419
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at efee0000 [disabled] [size=128K]
        Capabilities: <access denied>

me@Northern-Pilgrim:~$ cat /proc/asound/cards
--- no soundcards ---
me@Northern-Pilgrim:~$ 

I have seen many threads and posts concerning sound card issues. Is this normal? Have previous versions also had issues?
HELP!
Northern Pilgrim

---


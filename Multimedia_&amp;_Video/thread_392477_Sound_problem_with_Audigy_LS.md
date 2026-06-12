---
title: "Sound problem with Audigy LS"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by WetWired on 2007-03-24
My sound does work, but I am unable to adjust the volume with any tools inside ubuntu. I can turn the speakers down, but nothing else works. I'm not sure why. Anyone else having this problem?

---

### Post by WetWired on 2007-03-24
Here's this, if it will help.

> robbie@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
        Subsystem: Intel Corporation Unknown device 2580
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: cdf00000-cfffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dff00000
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: cde00000-cdefffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 8000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at 8400 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at 8800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 9000 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 233
        Memory at cddff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 2601
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 225
        I/O ports at a800 [size=8]
        I/O ports at a400 [size=4]
        I/O ports at a000 [size=8]
        I/O ports at 9800 [size=4]
        I/O ports at 9400 [size=16]
        Memory at cddffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8179
        Flags: medium devsel, IRQ 5
        I/O ports at 0400 [size=32]

01:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 64, IRQ 217
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at cdefc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at c800 [size=256]
        Expansion ROM at cdec0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2221
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at cf000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at ce000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at e800 [size=128]
        [virtual] Expansion ROM at cdfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

robbie@ubuntu:~$ 


---

### Post by WetWired on 2007-03-24
Ok, I changed nothing, rebooted, and now I have no sound. I guess Ubuntu just doesn't like audigy cards.

---

### Post by Daveth on 2007-03-25
you using Alsa? My Audigy2 works just fine under it. Also, have you loaded gnome-alsa mixer, as it has master volume control there. Just a thought

---

### Post by Jellus on 2007-06-23
Hi i have the same problem ..  look here

mayan@mayan-desktop:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
        Subsystem: nVidia Corporation Unknown device cb84
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at cc00 [size=64]
        I/O ports at 5000 [size=64]
        I/O ports at 6000 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at ddefb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at ddefac00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ddef9000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at c480 [size=8]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7309
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at c400 [size=8]
        I/O ports at c080 [size=4]
        I/O ports at c000 [size=8]
        I/O ports at bc00 [size=4]
        I/O ports at b880 [size=16]
        Memory at ddef8000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: ddf00000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
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
        Capabilities: <access denied>

01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at df000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at de000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at ec00 [size=128]
        [virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
        Capabilities: <access denied>


The only thing that works with it is normal sound .. midi doesnt work ... 

mayan@mayan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

it is listed as device ca0106 ... older audigy cards use emu10k2 i believe ... ubuntu feisty doesnt give me midi capabilities sadly out of the box ... sad but true .. it might not only be just on ubuntu though ... doest cheer me up much though ... :)

Cheers,

Jellus

---


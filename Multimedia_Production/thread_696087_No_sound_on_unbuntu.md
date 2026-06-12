---
title: "No sound on unbuntu"
date: 2008-02-13
forum: Multimedia Production
---

### Post by kastelo on 2008-02-13
hello friends

i've done an pacage update to my ubuntu and wen i've rebooted my computer the sound dosen't work and i tipede on a shell:


> aplay -l

```
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: CA0106 [CA0106], dispositivo 0: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: CA0106 [CA0106], dispositivo 1: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: CA0106 [CA0106], dispositivo 2: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: CA0106 [CA0106], dispositivo 3: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

> lspci -v
 ```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at ff00 [size=32]
        I/O ports at 4c00 [size=64]
        I/O ports at 4c40 [size=64]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at febfe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fb00 [size=16]
        Capabilities: <access denied>

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at f600 [size=16]
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7100
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at f100 [size=16]
        Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe900000-fe9fffff
        Prefetchable memory behind bridge: fea00000-feafffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. MSI K8N Diamond
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at febf9000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f000 [size=8]
        Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe800000-fe8fffff
        Prefetchable memory behind bridge: 00000000fe700000-00000000fe7fffff
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fe600000-fe6fffff
        Prefetchable memory behind bridge: 00000000fe500000-00000000fe5fffff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fe400000-fe4fffff
        Prefetchable memory behind bridge: 00000000fe300000-00000000fe3fffff
        Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: 00000000b0000000-00000000cfffffff
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

01:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at df00 [size=64]
        Capabilities: <access denied>

01:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at de00 [size=8]
        Capabilities: <access denied>

01:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at fe9ff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fe9f8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: Unknown device 0574:086c
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 19
        Memory at fe9fe000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at dd00 [size=128]
        Capabilities: <access denied>

01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Micro-Star International Co., Ltd. K8N Diamond
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8209
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at c0000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

wat hapens 

ps: ji've done this too many times and it din't work  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

my ubunut is 64 bit's

---

### Post by kastelo on 2008-02-15
Solved can close

---

### Post by IF-Rit on 2008-02-17
Try to install Alsa Mixer and then turn off the surrond...

---


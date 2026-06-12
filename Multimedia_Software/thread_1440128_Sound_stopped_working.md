---
title: "Sound stopped working"
date: 2010-03-27
forum: Multimedia Software
---

### Post by gogofletch on 2010-03-27
I recently set up a dual boot system with Ubuntu 9.10 and WinXP. Everything was working fine until randomly the sound stopped working in Ubuntu, still fine in XP. I have followed every thread I can find about sound problems with no success. HELP!

the output of 'lspci -v' is:
```

andrew@andrew-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 80a3
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64
    Kernel modules: amd64-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: f9100000-fd2fffff
    Prefetchable memory behind bridge: d1000000-f0ffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 808a
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at fdd00000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at d400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 80f5
    Flags: bus master, 66MHz, medium devsel, latency 96, IRQ 18
    I/O ports at e400 [size=64]
    I/O ports at e000 [size=16]
    I/O ports at d800 [size=128]
    Memory at fdf00000 (32-bit, non-prefetchable) [size=4K]
    Memory at fde00000 (32-bit, non-prefetchable) [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sata_promise

00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
    Subsystem: ASUSTeK Computer Inc. Device 811a
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at fdc00000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at d000 [size=256]
    Expansion ROM at fdb00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: skge
    Kernel modules: skge

00:0c.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
    Subsystem: VIA Technologies Inc. Device 2403
    Flags: bus master, medium devsel, latency 64, IRQ 17
    I/O ports at c800 [size=32]
    I/O ports at c400 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ICE1724
    Kernel modules: snd-ice1724

00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
    Subsystem: Creative Labs Device 8027
    Flags: bus master, medium devsel, latency 64, IRQ 19
    I/O ports at b800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

00:0e.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
    Subsystem: Creative Labs Device 0020
    Flags: bus master, medium devsel, latency 64
    I/O ports at c000 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at b400 [size=8]
    I/O ports at b000 [size=4]
    I/O ports at a800 [size=8]
    I/O ports at a400 [size=4]
    I/O ports at a000 [size=16]
    I/O ports at ec00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 32, IRQ 20
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at ac00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at bc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at cc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at dc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at fda00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
    Subsystem: ASUSTeK Computer Inc. Device 80ed
    Flags: bus master, stepping, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
    Subsystem: ASUSTeK Computer Inc. Device 80b0
    Flags: medium devsel, IRQ 22
    I/O ports at 1000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
    Flags: medium devsel, IRQ 22
    I/O ports at 1400 [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-via82xx-modem

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 81b1
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fd200000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb
```

Thanks in advance.

---

### Post by Gregorybekkers on 2010-03-27
Do u have alsa mixer installed?

---

### Post by gogofletch on 2010-03-27
Yes...I have uninstalled/reinstalled it like 5 times now... :/

---

### Post by b33tfr33kr on 2010-03-27
when that happened to me i was able to fix it by re-initializing my devices. try "alsactl init"

---

### Post by gogofletch on 2010-03-27
That gave me an interesting output....


```
andrew@andrew-desktop:~$ alsactl init
Unknown hardware: "VIA8237" "Analog Devices AD1980" "AC97a:41445370" "0x1043" "0x80b0"
Hardware is initialized using a guess method
/usr/share/alsa/init/default:51: control element not found
/usr/share/alsa/init/default:52: missing closing brace for format
/usr/share/alsa/init/default:52: error parsing CTL attribute
/usr/share/alsa/init/default:52: invalid rule
```

...still no sound

---

### Post by gogofletch on 2010-03-27
Got it. It seems that my 7.1 card isn't fully supported, and Ubuntu only treats it as a "Stereo Duplex" and will not play in any other setting.

---


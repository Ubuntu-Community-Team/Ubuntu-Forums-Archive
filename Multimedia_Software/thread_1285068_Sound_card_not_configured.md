---
title: "Sound card not configured"
date: 2009-10-07
forum: Multimedia Software
---

### Post by swappo1 on 2009-10-07
I get an error when trying to play a cd or adjust the volume control.  Its says I don't have the right gstreamer plugins or my sound card is not configured.  This is a new install so I don't think sound card is configured.  Here is my info.
lspci -v
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0
   Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0
   I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: 66MHz, fast devsel, IRQ 10
   I/O ports at 2900 [size=64]
   I/O ports at 2d00 [size=64]
   I/O ports at 2e00 [size=64]
   Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
   Memory at fce80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
   Memory at fce7f000 (32-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: ohci_hcd
   Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
   Memory at fce7ec00 (32-bit, non-prefetchable) [size=256]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd
   Kernel modules: ehci-hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
   Memory at fce7d000 (32-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: ohci_hcd
   Kernel modules: ohci-hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
   Memory at fce7e800 (32-bit, non-prefetchable) [size=256]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd
   Kernel modules: ehci-hcd

00:07.0 Audio device: nVidia Corporation Device 0774 (rev a1)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
   Memory at fce78000 (32-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01 [Subtractive decode])
   Flags: bus master, 66MHz, fast devsel, latency 0
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
   Memory behind bridge: fcf00000-fcffffff
   Capabilities: <access denied>

00:09.0 RAID bus controller: nVidia Corporation Device 0ad8 (rev a2)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 1275
   I/O ports at d480 [size=8]
   I/O ports at d400 [size=4]
   I/O ports at d080 [size=8]
   I/O ports at d000 [size=4]
   I/O ports at cc00 [size=16]
   Memory at fce76000 (32-bit, non-prefetchable) [size=8K]
   Capabilities: <access denied>
   Kernel driver in use: ahci
   Kernel modules: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 1274
   Memory at fce7c000 (32-bit, non-prefetchable) [size=4K]
   I/O ports at c880 [size=8]
   Memory at fce7e400 (32-bit, non-prefetchable) [size=256]
   Memory at fce7e000 (32-bit, non-prefetchable) [size=16]
   Capabilities: <access denied>
   Kernel driver in use: forcedeth
   Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
   I/O behind bridge: 0000e000-0000efff
   Memory behind bridge: fd000000-febfffff
   Prefetchable memory behind bridge: 00000000e6000000-00000000efffffff
   Capabilities: <access denied>
   Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation Device 077a (rev a1) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1) (prog-if 00 [Normal decode])
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
   Flags: fast devsel
   Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
   Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
   Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
   Flags: fast devsel
   Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
   Flags: fast devsel

01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, medium devsel, latency 32, IRQ 19
   Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
   Capabilities: <access denied>
   Kernel driver in use: ohci1394
   Kernel modules: ohci1394

02:00.0 VGA compatible controller: nVidia Corporation Device 0847 (rev a2) (prog-if 00 [VGA controller])
   Subsystem: Hewlett-Packard Company Device 2a81
   Flags: bus master, fast devsel, latency 0, IRQ 20
   Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
   Memory at e8000000 (64-bit, prefetchable) [size=128M]
   Memory at e6000000 (64-bit, prefetchable) [size=32M]
   I/O ports at ec00 [size=128]
   [virtual] Expansion ROM at febe0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: nvidia
   Kernel modules: nvidia, nvidiafb

```
lsmod | grep snd
```
snd_hda_intel         436696  0
snd_pcm                81800  1 snd_hda_intel
snd_seq                54304  0
snd_timer              25744  2 snd_pcm,snd_seq
snd_seq_device         11668  1 snd_seq
snd                    63688  5 snd_hda_intel,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12064  1 snd
snd_page_alloc         13072  2 snd_hda_intel,snd_pcm
```
lspci | grep Audio
```
00:07.0 Audio device: nVidia Corporation Device 0774 (rev a1)
```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Any ideas as to what I need to do to configure sound card?

---


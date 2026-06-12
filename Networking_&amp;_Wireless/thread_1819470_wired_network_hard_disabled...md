---
title: "wired network hard disabled..?"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by homemadev on 2011-08-06
I had a new computer.. only wired network was functional.. then I got the wireless working.. then I added XBMC.. then wireless and wired networking stopped working.. so I removed XBMC.. I ran from liveCD... I reinstalled... still no wired network?! All I can figure is that something changed in the BIOS or on the hardware.. or it is just a POS..? Thanks for any help! :)

Here's what I know:
Atom 330
Ubuntu Natty

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:68:76:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
``````
$ sudo ifdown eth0
ifdown: interface eth0 not configured
``````
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
``````
$ uname -r
2.6.38-10-generic
``````
$ sudo lspci -v
[sudo] password for fred: 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 4f00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: 66MHz, fast devsel, IRQ 10
    I/O ports at 4900 [size=64]
    I/O ports at 4d00 [size=64]
    I/O ports at 4e00 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fae80000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fae7d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fae7e800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
    Subsystem: nVidia Corporation Device cb84
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Capabilities: [b8] Subsystem: nVidia Corporation Device cb79

00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1) (prog-if 85 [Master SecO PriO])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 41
    I/O ports at c080 [size=8]
    I/O ports at c000 [size=4]
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=16]
    Memory at fae76000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Capabilities: [8c] SATA HBA v1.0
    Capabilities: [b0] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: ahci
    Kernel modules: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: [40] Subsystem: nVidia Corporation Device cb79
    Capabilities: [48] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: faf00000-fbffffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000f7ffffff
    Capabilities: [40] Subsystem: nVidia Corporation Device cb79
    Capabilities: [48] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000f9f00000-00000000f9ffffff
    Capabilities: [40] Subsystem: nVidia Corporation Device cb79
    Capabilities: [48] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: [40] Subsystem: nVidia Corporation Device cb79
    Capabilities: [48] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: [40] Subsystem: nVidia Corporation Device cb79
    Capabilities: [48] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Capabilities: [40] Subsystem: nVidia Corporation Device cb79
    Capabilities: [48] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/2 Maskable- 64bit+
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport
    Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1) (prog-if 00 [VGA controller])
    Subsystem: nVidia Corporation Device cb79
    Flags: bus master, fast devsel, latency 0, IRQ 23
    Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f6000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fafe0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at e800 [size=256]
    Memory at febff000 (64-bit, non-prefetchable) [size=4K]
    Memory at f9ffc000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number eb-02-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---


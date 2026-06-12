---
title: "Wireless keeps dropping"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Kales on 2010-01-10
I'm running Ubuntu 9.10 KK, using wireless internet (as you've probably already gathered). Every so often my wireless will drop, and the box asking for the key appears. However, it won't reconnect (no matter how long I wait, or how many times I enter the pass), until I restart my computer.

This has been going on for as long as I've had Ubuntu 9.10, no network changes have been made prior to the problem.

If any additional information is needed, let me know :) Thanks in advance.

---

### Post by The Toxic Mite on 2010-01-10
Why hello there! :)
 
Can you go to Applications --> Accessories --> Terminal, and enter the following commands please?
 
```

sudo lshw -c network
lspci -v less
iwconfig

```
 
Post the outputs here when done :)
 
-TTM-

---

### Post by Kales on 2010-01-10
Thanks for the reply.

lshw -c network:
```
root@owner-desktop:/home/owner# lshw -c network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:22:15:06:f9:86
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:29 memory:f9e7c000-f9e7cfff ioport:c880(size=8) memory:f9e7e400-f9e7e4ff memory:f9e7e000-f9e7e00f
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: ra0
       version: 00
       serial: 00:16:44:d6:1f:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.101 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:fe9f0000-fe9fffff
```

lspci -v:
```
root@owner-desktop:/home/owner# lspci -v
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: [94] HyperTransport: #1a
    Capabilities: [60] HyperTransport: Retry Mode
    Capabilities: [44] HyperTransport: Slave or Primary Interface
    Capabilities: [d0] HyperTransport: #1c

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 2f00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: 66MHz, fast devsel, IRQ 7
    I/O ports at 2900 [size=64]
    I/O ports at 2d00 [size=64]
    I/O ports at 2e00 [size=64]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
    Memory at f9e80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at f9e7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at f9e7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at f9e7d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f9e7e800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [44] Debug port: BAR=1 offset=00a0
    Capabilities: [80] Power Management version 2
    Kernel driver in use: ehci_hcd

00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at f9e78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Memory behind bridge: f9f00000-f9ffffff
    Capabilities: [b8] Subsystem: Hewlett-Packard Company Device 2a6e
    Capabilities: [8c] HyperTransport: MSI Mapping Enable+ Fixed-

00:09.0 RAID bus controller: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (RAID mode) (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 28
    I/O ports at d480 [size=8]
    I/O ports at d400 [size=4]
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=16]
    Memory at f9e76000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [44] Power Management version 2
    Capabilities: [8c] SATA HBA <?>
    Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable+
    Capabilities: [ec] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 29
    Memory at f9e7c000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at c880 [size=8]
    Memory at f9e7e400 (32-bit, non-prefetchable) [size=256]
    Memory at f9e7e000 (32-bit, non-prefetchable) [size=16]
    Capabilities: [44] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/4 Enable+
    Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-fe8fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [40] Subsystem: Hewlett-Packard Company Device 2a6e
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: [40] Subsystem: Hewlett-Packard Company Device 2a6e
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: [40] Subsystem: Hewlett-Packard Company Device 2a6e
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Memory behind bridge: fea00000-febfffff
    Capabilities: [40] Subsystem: Hewlett-Packard Company Device 2a6e
    Capabilities: [48] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
    Capabilities: [60] HyperTransport: MSI Mapping Enable+ Fixed-
    Capabilities: [80] Express Root Port (Slot+), MSI 00
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a6e
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 9008
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at fe8e0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

04:00.0 Network controller: RaLink RT2860
    Subsystem: Lite-On Communications Inc Device 7600
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta

05:00.0 Multimedia video controller: Conexant Systems, Inc. Hauppauge Inc. HDPVR-1250 model 1196 (rev 0f)
    Subsystem: Hauppauge computer works Inc. Device 7801
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 2
    Capabilities: [90] Vital Product Data <?>
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [200] Virtual Channel <?>
    Kernel driver in use: cx23885
    Kernel modules: cx23885
```

iwconfig:
```
root@owner-desktop:/home/owner# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"wireless"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1C:10:18:93:8C   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:EAC4-2940-A149-8EAF-3815-AD67-3486-8F82
          Link Quality=84/100  Signal level:-58 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

There ya go, also I've tried installing backport modules as this post suggests (same problem, yes I know the backports were meant for Atheros but I thought I'd give it a try anyway..no help): [http://ubuntuforums.org/showthread.php?t=1333994&page=2](http://ubuntuforums.org/showthread.php?t=1333994&page=2)

---


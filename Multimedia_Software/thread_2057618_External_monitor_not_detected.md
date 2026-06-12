---
title: "External monitor not detected"
date: 2012-09-14
forum: Multimedia Software
---

### Post by miniCruzer on 2012-09-14
Just installed Lubuntu 12.04 on my laptop that was running the same version of Ubuntu a few weeks ago.

I used to be able to connect my TV via the HDMI output on my computer in Ubuntu and it would work fine. There is a key on my keyboard that allows for dual monitor options to change (clone, extended, projector only, etc.).

Now it won't even read the HDMI port. When I plug the TV in, instead of the usual NO SIGNAL, it says Check signal cable. I might have a bad cable but I don't want to buy a new one before I've identified the real issue.

Output of xrandr --verbose:

```
sam@insanity:~$ xrandr --verbose
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 900, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 (0x138) normal (normal) 0mm x 0mm
    Identifier: 0x137
    Timestamp:  29608
    Subpixel:   horizontal rgb
    Clones:    
    CRTC:       0
    CRTCs:      0
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
  1600x900 (0x138)    0.0MHz *current
        h: width  1600 start    0 end    0 total 1600 skew    0 clock    0.0KHz
        v: height  900 start    0 end    0 total  900           clock    0.0Hz

```

# lspci -v
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9649 (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3566
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel modules: radeon

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0200000-f02fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f04fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] Device 1234
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 40
    I/O ports at 4118 [size=8]
    I/O ports at 4124 [size=4]
    I/O ports at 4110 [size=8]
    I/O ports at 4120 [size=4]
    I/O ports at 4100 [size=16]
    Memory at f034e000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [50] MSI: Enable+ Count=1/16 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034d000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034c000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f034b000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f034a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=64

00:16.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at f0349000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at f0348000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    Flags: fast devsel

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    Flags: fast devsel

00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    Flags: fast devsel

00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    Flags: fast devsel

00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    Flags: fast devsel

01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 1629
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
    Kernel driver in use: rtl8192ce
    Kernel modules: rtl8192ce

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at 2000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
    Subsystem: Hewlett-Packard Company Device 3568
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f0100000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at f0400000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor


```

I can't find much help with Google, and the wikipedia article doesn't explain this very well to me. Apparently it should "JUST WORK"

---

### Post by marinara on 2012-09-14
this is just a guess, but you haven't installed the ati drivers?

---


---
title: "Internet connection doesn't always work"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by zaab9 on 2013-02-05
Hi guys,

I'm new to the whole forum thing but I've used Ubuntu for a while then switched to Fedora 17 and then back to Ubuntu after Fedora 18 came out. The whole reason I stopped using Ubuntu the first time is because it gives me problems with the Internet connection. Either it will be extremely slow some times or other times it will completely shut off for a few seconds and then come right back on. Any tips n tricks would be great and if you need any data from my comp to help me just let me know and I can post what ever you need.  I don't really know exactly what I'm doing in the terminal but I have no problem copying and pasting code ;).

Thanks!

---

### Post by zaab9 on 2013-02-05
Oh ya, I'm running 12.10

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by zaab9 on 2013-02-05
PCI (sysfs)

---

### Post by zaab9 on 2013-02-05
*-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:c5:23:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.5.0-17-generic firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:d3400000-d3403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:e3:83:6c
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by zaab9 on 2013-02-05
Well I downloaded this file  LINUX driver for kernel 3.x and 2.6.x and 2.4.x from this page [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Then followed these instructions
[https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

And got these results 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4050 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d4406100 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at d4405c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d3400000-d43fffff
    Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2400000-d33fffff
    Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at d4405800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 4048 [size=8]
    I/O ports at 405c [size=4]
    I/O ports at 4040 [size=8]
    I/O ports at 4058 [size=4]
    I/O ports at 4020 [size=32]
    Memory at d4405000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: medium devsel, IRQ 10
    Memory at d4406000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d4404000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
    Subsystem: Hewlett-Packard Company Device 1467
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at d3400000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: rtl8192se
    Kernel modules: rtl8192se

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 2000 [size=256]
    Memory at d1410000 (64-bit, prefetchable) [size=4K]
    Memory at d1400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1420000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: r8169

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Hewlett-Packard Company Device 1425
    Flags: bus master, fast devsel, latency 0

Didn't work correct?

---

### Post by zaab9 on 2013-02-06
Tried again got the same results

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by zaab9 on 2013-02-06
Ya this was all wireless, right now I'm working on a lab report and I'll try it later tonight. Thanks a ton for all this help by the way.

---


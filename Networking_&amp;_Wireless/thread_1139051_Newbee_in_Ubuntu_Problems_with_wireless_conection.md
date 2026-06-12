---
title: "Newbee in Ubuntu: Problems with wireless conection"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by bancorat on 2009-04-26
Hi guys,

I just installed Ubuntu 9.04 in my laptop.  I have an HP dv5020.  I've been trying to connect to my wireless network with no luck.  I don't know if its the driver or if I'm not doing something, in the terminal I used / $ lspci -v and this is what I get.

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 64
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
    Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
    Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
    Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: 66MHz, medium devsel
    I/O ports at 8400 [size=16]
    Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0200000-c02fffff

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem

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

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at c8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeonfb

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 1355
    Flags: bus master, fast devsel, latency 64, IRQ 21
    Memory at c0200000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 30a4
    Flags: bus master, medium devsel, latency 128, IRQ 22
    I/O ports at a000 [size=256]
    Memory at c0202000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp


When I click the two computers in the top right part of my desktop, On wireless networks it doesn't have anything and in Wired Network it says Auto eth0.  Sometimes under  wireless network it says's device not ready.

Is there a way that I can delete my driver and install it again, or what other options do I have?  

Thanks a lot!

---

### Post by t0mppa on 2009-04-26
Hey, welcome aboard Ubuntu. Don't worry about doing something wrong, wireless is pretty easy on Ubuntu, long as you don't go manually editing the config files (doesn't sound like you did that), you can hardly do anything wrong. There just are a large number of different wireless chips around and almost all of them require different configuration, meaning they don't always work out of the box.

Personally I can't help with broadcom chips, but there's lots of threads about them lying around, if you do a search on your chip specifics, there's a good chance you'll find others who've been in the same situation.

If you feel you need hand-to-hand type of instructions, just stick to this thread and someone who knows about broadcom chips will likely take it up fairly soon. In the mean time, here's some things to note:

> **bancorat said:**
> 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Kernel driver in use: b43-pci-bridge

That's all the info you need here from the lspci. Other useful information for diagnosing the issue can be provided by running following commands on the terminal:```
iwconfig
iwlist scan
lshw -C network
```

---

### Post by bancorat on 2009-04-27
Thanks for the advice.  I'll try to find more info on the forum. Thanks!

---


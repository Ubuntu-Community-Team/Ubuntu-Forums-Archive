---
title: "Can't get Dell Inspiron 1300 to use wireless"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by netjjordan on 2011-01-04
Hi

I have an Inspiron 1300 and have followed the "B43" instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

Plus various other guides including the "one click b43 fix" but nothing useful happens. Wired access doesn't work either.

I was advised to post the output of lspci -v so here it is:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at eff8 [size=8]
Memory at c0000000 (32-bit, prefetchable) [size=256M]
Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0
Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0, IRQ 42
Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
I/O behind bridge: 00002000-00002fff
Memory behind bridge: 20000000-201fffff
Prefetchable memory behind bridge: 0000000020200000-00000000203fffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: dfc00000-dfdfffff
Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at bf80 [size=32]
Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at bf60 [size=32]
Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at bf40 [size=32]
Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at bf20 [size=32]
Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 16
Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
Memory behind bridge: dfb00000-dfbfffff
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0
Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at bfa0 [size=16]
Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 64, IRQ 18
Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: b44
Kernel modules: b44

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card
Flags: bus master, fast devsel, latency 64, IRQ 17
Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

Thanks for any help, Julian

---

### Post by netjjordan on 2011-01-04
Hi

I have an Inspiron 1300 and have followed the "B43" instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")

Plus various other guides including the "one click b43 fix" but nothing useful happens. Wired access doesn't work either.

I was advised to post the output of lspci -v so here it is:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: agpgart-intel
Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
I/O ports at eff8 [size=8]
Memory at c0000000 (32-bit, prefetchable) [size=256M]
Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0
Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 0, IRQ 42
Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
I/O behind bridge: 00002000-00002fff
Memory behind bridge: 20000000-201fffff
Prefetchable memory behind bridge: 0000000020200000-00000000203fffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: dfc00000-dfdfffff
Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
Capabilities: <access denied>
Kernel driver in use: pcieport
Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at bf80 [size=32]
Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 17
I/O ports at bf60 [size=32]
Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 18
I/O ports at bf40 [size=32]
Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 19
I/O ports at bf20 [size=32]
Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 16
Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
Memory behind bridge: dfb00000-dfbfffff
Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0
Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
Subsystem: Dell Device 01c9
Flags: bus master, medium devsel, latency 0, IRQ 16
I/O ports at 01f0 [size=8]
I/O ports at 03f4 [size=1]
I/O ports at 0170 [size=8]
I/O ports at 0374 [size=1]
I/O ports at bfa0 [size=16]
Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
Subsystem: Dell Device 01c9
Flags: bus master, fast devsel, latency 64, IRQ 18
Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: b44
Kernel modules: b44

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card
Flags: bus master, fast devsel, latency 64, IRQ 17
Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb
```

Thanks for any help, Julian

---

### Post by spiky001 on 2011-01-04
Can you run pc on live cd with eth0 cable in will it work then?

---

### Post by cariboo on 2011-01-04
Merged two threads, netjjordan is you want one post removed please report it.

---

### Post by netjjordan on 2011-01-04
Hi

It is a live USB boot (does that make any difference?) - have just tested this with a cable but no luck. The "Auto Eth0" ticks away for a few seconds and then does nothing. Thanks

---


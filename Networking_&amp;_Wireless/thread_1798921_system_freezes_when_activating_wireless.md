---
title: "system freezes when activating wireless"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by cjimenez2581 on 2011-07-06
My laptop is a Toshiba satellite C655D-S5133 Im using ubuntu 11.04, previous version there is not driver now It doesnt work...

 It woks great with wired




I post the result of lsusb -v and it is:


00:00.0 Host bridge: Advanced Micro Devices [AMD] Pavilion DM1Z-3000 Host bridge
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 0
 00:01.0 VGA compatible controller: ATI Technologies Inc Device 9803 (prog-if 00 [VGA controller])
        Subsystem: Toshiba America Info Systems Device fde8
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at 80000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=256]
        Memory at 90300000 (32-bit, non-prefetchable) [size=256K]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon
 00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at 4138 [size=8]
        I/O ports at 414c [size=4]
        I/O ports at 4130 [size=8]
        I/O ports at 4148 [size=4]
        I/O ports at 4110 [size=16]
        Memory at 9034a000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci
 00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at 90349000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd
 00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at 90348000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
 00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at 90347000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd
 00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at 90346000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: 66MHz, medium devsel
        Kernel driver in use: piix4_smbus
        Kernel modules: sp5100_tco, i2c-piix4
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at 90340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
 00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 0
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Kernel modules: shpchp
 00:15.0 PCI bridge: ATI Technologies Inc Device 43a0 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: 90200000-902fffff
        Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp
 00:15.1 PCI bridge: ATI Technologies Inc Device 43a1 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 90100000-901fffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp
 00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at 90345000 (32-bit, non-prefetchable) [size=4K]
        Kernel driver in use: ohci_hcd
 00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at 90344000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
 00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
        Flags: fast devsel
 00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
        Flags: fast devsel
 00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
        Flags: fast devsel
 00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
        Flags: fast devsel
        Capabilities: <access denied>
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
 [B]02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at 3000 [size=256]
        Memory at 90200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: rtl8192ce
        Kernel modules: rtl8192ce[/B]
 06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, fast devsel, latency 0, IRQ 40
        Memory at 90100000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: atl1c
        Kernel modules: atl1c


Thansk for any help you can brings...

---


---
title: "Laptop, No sound"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by JNowka on 2007-02-08
I recently have bought a laptop, and when I initially install kubuntu 6.10 I had sound, but after awhile, I no longer have sound.  I have checked with the alsamixer, I have tried using anything that I could think of, I have even reinstall most, if not all of the stuff that allows sound on computer, but with no success. The following is some info about my sound.  Any help will be greatly appreciated.

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: Conexant Analog Audio [Conexant Analog Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0
        Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at d8240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3f00000
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d4000000-d5ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1f00000
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 217
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 217
        Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: d8000000-d80fffff
        Capabilities: [50] #0d [0000]

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 209
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 4
        I/O ports at 18c0 [size=32]

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number 54-3f-37-ff-ff-d2-19-00

05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d8001000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

05:05.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 64, IRQ 169
        Memory at d8001800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

05:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 3
        Memory at d8001c00 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 3
        Memory at d8002000 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 3
        Memory at d8002400 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 64, IRQ 233
        Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 4000 [size=64]
        Capabilities: [dc] Power Management version 2

---


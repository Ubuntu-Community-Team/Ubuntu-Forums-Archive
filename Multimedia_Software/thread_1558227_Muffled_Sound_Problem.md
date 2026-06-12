---
title: "Muffled Sound Problem"
date: 2010-08-21
forum: Multimedia Software
---

### Post by pierce_g on 2010-08-21
I'm running Lucid and as of today my audio sounds really muffled, like I'm listening to everything through a pillow. I've had this installation for months and the problem only started today. The last thing I remember doing before the problem started was watching a .mpg movie in VLC.

I'm not really sure what information would be useful, but maybe these will be a good start.
```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

sudo lspci -v
[sudo] password for pierce: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 02be
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fc000000-fc0fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [88] Subsystem: Dell Device 02be
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [140] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1800 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1820 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at fc504800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fc500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f6000000-f7ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f8000000-f9ffffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: fa000000-fbffffff
    Prefetchable memory behind bridge: 00000000f4000000-00000000f5ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: fc100000-fc1fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000c01fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1860 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1880 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18a0 [size=32]
    Capabilities: [50] PCIe advanced features <?>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fc504c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCIe advanced features <?>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
    Memory behind bridge: fc200000-fc2fffff
    Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Dell Device 02be
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
    I/O ports at 18f0 [size=8]
    I/O ports at 18e4 [size=4]
    I/O ports at 18e8 [size=8]
    I/O ports at 18e0 [size=4]
    I/O ports at 18c0 [size=32]
    Memory at fc504000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA <?>
    Capabilities: [b0] PCIe advanced features <?>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 02be
    Flags: medium devsel, IRQ 10
    Memory at c0200000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
    Subsystem: Dell Device 02be
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 2000 [size=256]
    Memory at fc000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at fc020000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV710/730
    Subsystem: Dell Device 02be
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fc010000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [100] Vendor Specific Information <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1321
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number ca-83-9c-ff-ff-fb-22-00
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
    Subsystem: Dell Device 02be
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at fc100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [48] Power Management version 3
    Capabilities: [40] Vital Product Data <?>
    Capabilities: [60] Vendor Specific Information <?>
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [cc] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 22-34-fa-fe-ff-19-22-00
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: tg3
    Kernel modules: tg3

09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 32, IRQ 17
    Memory at fc200000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fc200800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at fc200c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Dell Device 02be
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at fc201000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2

```Please let me know what other information would be useful.

Thanks.

---

### Post by pierce_g on 2010-08-22
Also, I get normal sounding audio from headphones.

---

### Post by jmfal on 2010-08-22
Welcome to ubuntu

open a terminal: applications>accessories>terminal, and enter

           ```
   alsamixer
```
make sure all your volume controls are not muted, pcm should be 75-100%
use l/r arrows on keypad to change selections up/down to change settings

I see your have hda snd, I bumped a thread to the top that you should look at
>markbuntu: hda-snd<

I think you need to add/edit some script,

---

### Post by pierce_g on 2010-08-22
I've already checked alsamixer and everything looked fine.

---


---
title: "Hauppauge WinTV-HVR 4400-HD fails to install"
date: 2014-06-19
forum: Multimedia Software
---

### Post by jonathan-l-harrison on 2014-06-19
I am running a PC with INtel 7i Quad core processor, 32G RAM and 1 Tb HD with Ubuntu 14:04  I tend to nuse xfce.

I have bought and plugged in a Hauppauge WinTV-HVR 4400-HD fails to install TV and Satelite card, but I can not get my PC to recognise it.  Can anyone help, please????

---

### Post by xc3RnbFO8P on 2014-06-19
There is only bad news about this card [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4400#Making_it_Work]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4400#Making_it_Work")
you can do **dmesg** in terminal to be sure

---

### Post by jonathan-l-harrison on 2014-06-21
Ringi
Sorry for not getting back.  Didn't realise you had left a message.  I am not getting the alerts.  I will try dmesg.  What am I looking for?

---

### Post by xc3RnbFO8P on 2014-06-21
Output like this:
> [    2.680305] cx23885 driver version 0.0.3 loaded
[    2.680607] CORE cx23885[0]: subsystem: 0070:c108, board: Hauppauge WinTV-HVR4400 [card=38,autodetected]
[    3.005418] cx23885[0]: warning: unknown hauppauge model #121019
[    3.005419] cx23885[0]: hauppauge eeprom: model=121019
[    3.005421] cx23885_dvb_register() allocating 1 frontend(s)
[    3.005422] cx23885[0]: cx23885 based dvb card
[    3.013145] DVB: registering new adapter (cx23885[0])
[    3.013149] cx23885 0000:01:00.0: DVB: registering adapter 0 frontend 0 (NXP TDA10071)...
[    3.013324] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    3.013329] cx23885[0]/0: found at 0000:01:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xf7c00000

---

### Post by jonathan-l-harrison on 2014-06-21
Are these of any interest?
Result of "sudo lspci -vn :

```
    ]00:02.0 0604: 8086:0e04 (rev 04) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: [40] Subsystem: 1043:84ef
    Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Capabilities: [110] Access Control Services
    Capabilities: [148] Advanced Error Reporting
    Capabilities: [1d0] Vendor Specific Information: ID=0003 Rev=1 Len=00a <?>
    Capabilities: [250] #19
    Capabilities: [280] Vendor Specific Information: ID=0005 Rev=3 Len=018 <?>
    Kernel driver in use: pcieport

00:03.0 0604: 8086:0e08 (rev 04) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: [40] Subsystem: 1043:84ef
    Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Capabilities: [110] Access Control Services
    Capabilities: [148] Advanced Error Reporting
    Capabilities: [1d0] Vendor Specific Information: ID=0003 Rev=1 Len=00a <?>
    Capabilities: [250] #19
    Capabilities: [280] Vendor Specific Information: ID=0005 Rev=3 Len=018 <?>
    Kernel driver in use: pcieport

00:03.2 0604: 8086:0e0a (rev 04) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-fb0fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f9ffffff
    Capabilities: [40] Subsystem: 1043:84ef
    Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
    Capabilities: [90] Express Root Port (Slot+), MSI 00
    Capabilities: [e0] Power Management version 3
    Capabilities: [100] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
    Capabilities: [110] Access Control Services
    Capabilities: [148] Advanced Error Reporting
    Capabilities: [1d0] Vendor Specific Information: ID=0003 Rev=1 Len=00a <?>
    Capabilities: [250] #19
    Capabilities: [280] Vendor Specific Information: ID=0005 Rev=3 Len=018 <?>
    Kernel driver in use: pcieport

00:05.0 0880: 8086:0e28 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:05.2 0880: 8086:0e2a (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:05.4 0800: 8086:0e2c (rev 04) (prog-if 20 [IO(X)-APIC])
    Subsystem: 1043:84ef
    Flags: bus master, fast devsel, latency 0
    Memory at fb12a000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [44] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [e0] Power Management version 3

00:11.0 0604: 8086:1d3e (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] Power Management version 3
    Capabilities: [88] Subsystem: 1043:84ef
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [138] Access Control Services
    Kernel driver in use: pcieport

00:16.0 0780: 8086:1d3a (rev 05)
    Subsystem: 1043:84ef
    Flags: bus master, fast devsel, latency 0, IRQ 102
    Memory at fb129000 (64-bit, non-prefetchable) [size=16]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: mei_me

00:19.0 0200: 8086:1503 (rev 06)
    Subsystem: 1043:849c
    Flags: bus master, fast devsel, latency 0, IRQ 98
    Memory at fb100000 (32-bit, non-prefetchable) [size=128K]
    Memory at fb128000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] PCI Advanced Features
    Kernel driver in use: e1000e

00:1a.0 0c03: 8086:1d2d (rev 06) (prog-if 20 [EHCI])
    Subsystem: 1043:84ef
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at fb127000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1b.0 0403: 8086:1d20 (rev 06)
    Subsystem: 1043:84f8
    Flags: bus master, fast devsel, latency 0, IRQ 101
    Memory at fb120000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel

00:1c.0 0604: 8086:1d10 (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Memory behind bridge: fb200000-fb3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.1 0604: 8086:1d12 (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: fb900000-fb9fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.2 0604: 8086:1d14 (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: fb800000-fb8fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.3 0604: 8086:1d16 (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: fb700000-fb7fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.4 0604: 8086:1d18 (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Memory behind bridge: fb600000-fb6fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.5 0604: 8086:1d1a (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fb500000-fb5fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1c.7 0604: 8086:1d1e (rev b6) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fb400000-fb4fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: 1043:84ef
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport

00:1d.0 0c03: 8086:1d26 (rev 06) (prog-if 20 [EHCI])
    Subsystem: 1043:84ef
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fb126000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci-pci

00:1e.0 0604: 8086:244e (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=32
    Capabilities: [50] Subsystem: 1043:84ef

00:1f.0 0601: 8086:1d41 (rev 06)
    Subsystem: 1043:84ef
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich

00:1f.2 0106: 8086:1d02 (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: 1043:84ef
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 96
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f020 [size=32]
    Memory at fb125000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci

00:1f.3 0c05: 8086:1d22 (rev 06)
    Subsystem: 1043:84ef
    Flags: medium devsel, IRQ 15
    Memory at fb124000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f000 [size=32]

04:00.0 0300: 10de:0de1 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: 196e:0828
    Flags: bus master, fast devsel, latency 0, IRQ 100
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f0000000 (64-bit, prefetchable) [size=128M]
    Memory at f8000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fb000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nouveau

04:00.1 0403: 10de:0bea (rev a1)
    Subsystem: 196e:0828
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fb080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel

06:00.0 0400: 14f1:8880 (rev 04)
    Subsystem: 0070:c108
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb200000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vital Product Data
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [200] Virtual Channel
    Kernel driver in use: cx23885

07:00.0 0c03: 1b21:1042 (prog-if 30 [XHCI])
    Subsystem: 1043:8488
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fb900000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: xhci_hcd

08:00.0 0c03: 1b21:1042 (prog-if 30 [XHCI])
    Subsystem: 1043:8488
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fb800000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: xhci_hcd

09:00.0 0c03: 1b21:1042 (prog-if 30 [XHCI])
    Subsystem: 1043:8488
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fb700000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: xhci_hcd

0a:00.0 0c03: 1b21:1042 (prog-if 30 [XHCI])
    Subsystem: 1043:8488
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb600000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [50] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [68] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: xhci_hcd

0b:00.0 0106: 1b21:0612 (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: 1043:84b7
    Flags: bus master, fast devsel, latency 0, IRQ 97
    I/O ports at d050 [size=8]
    I/O ports at d040 [size=4]
    I/O ports at d030 [size=8]
    I/O ports at d020 [size=4]
    I/O ports at d000 [size=32]
    Memory at fb500000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: ahci

0c:00.0 0106: 1b21:0612 (rev 01) (prog-if 01 [AHCI 1.0])
    Subsystem: 1043:84b7
    Flags: bus master, fast devsel, latency 0, IRQ 99
    I/O ports at c050 [size=8]
    I/O ports at c040 [size=4]
    I/O ports at c030 [size=8]
    I/O ports at c020 [size=4]
    I/O ports at c000 [size=32]
    Memory at fb400000 (32-bit, non-prefetchable) [size=512]
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: ahci

ff:08.0 0880: 8086:0e80 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:09.0 0880: 8086:0e90 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0a.0 0880: 8086:0ec0 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0a.1 0880: 8086:0ec1 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0a.2 0880: 8086:0ec2 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0a.3 0880: 8086:0ec3 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0b.0 0880: 8086:0e1e (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0b.3 0880: 8086:0e1f (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0c.0 0880: 8086:0ee0 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0c.1 0880: 8086:0ee2 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0d.0 0880: 8086:0ee1 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0d.1 0880: 8086:0ee3 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0e.0 0880: 8086:0ea0 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:0e.1 1101: 8086:0e30 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Kernel driver in use: ivt_uncore

ff:0f.0 0880: 8086:0ea8 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.1 0880: 8086:0e71 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.2 0880: 8086:0eaa (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.3 0880: 8086:0eab (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.4 0880: 8086:0eac (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:0f.5 0880: 8086:0ead (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.0 0880: 8086:0eb0 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: ivt_uncore

ff:10.1 0880: 8086:0eb1 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: ivt_uncore

ff:10.2 0880: 8086:0eb2 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.3 0880: 8086:0eb3 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.4 0880: 8086:0eb4 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: ivt_uncore

ff:10.5 0880: 8086:0eb5 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Kernel driver in use: ivt_uncore

ff:10.6 0880: 8086:0eb6 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:10.7 0880: 8086:0eb7 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

ff:13.0 0880: 8086:0e1d (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:13.1 1101: 8086:0e34 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Kernel driver in use: ivt_uncore

ff:13.4 0880: 8086:0e81 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:13.5 1101: 8086:0e36 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel
    Kernel driver in use: ivt_uncore

ff:16.0 0880: 8086:0ec8 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:16.1 0880: 8086:0ec9 (rev 04)
    Subsystem: 1043:84ef
    Flags: fast devsel

ff:16.2 0880: 8086:0eca (rev 04)
    Subsystem: 1043:84e
    Flags: fast devsel

```


Result of "dmesg"

```

[    1.121401] nouveau  [  DEVICE][0000:04:00.0] BOOT0  : 0x0c1080a1

 [    1.121404] nouveau  [  DEVICE][0000:04:00.0] Chipset: GF108 (NVC1)
[    1.121405] nouveau  [  DEVICE][0000:04:00.0] Family : NVC0
[    1.122690] nouveau  [   VBIOS][0000:04:00.0] checking PRAMIN for image...
[    1.133275] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.174215] nouveau  [   VBIOS][0000:04:00.0] ... appears to be valid
[    1.174216] nouveau  [   VBIOS][0000:04:00.0] using image from PRAMIN
[    1.174281] nouveau  [   VBIOS][0000:04:00.0] BIT signature found
[    1.174283] nouveau  [   VBIOS][0000:04:00.0] version 70.08.29.00.01
[    1.174452] nouveau 0000:04:00.0: irq 100 for MSI/MSI-X
[    1.174458] nouveau  [     PMC][0000:04:00.0] MSI interrupts enabled
[    1.174479] nouveau W[     PFB][0000:04:00.0][0x00000000][ffff8807f3b04800] reclocking of this ram type unsupported
[    1.174481] nouveau  [     PFB][0000:04:00.0] RAM type: DDR3
[    1.174482] nouveau  [     PFB][0000:04:00.0] RAM size: 512 MiB
[    1.174483] nouveau  [     PFB][0000:04:00.0]    ZCOMP: 0 tags
[    1.178225] nouveau  [    VOLT][0000:04:00.0] GPU voltage: 900000uv
[    1.265759] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.265761] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.265899] hub 1-1:1.0: USB hub found
[    1.266007] hub 1-1:1.0: 6 ports detected
[    1.377499] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.377837] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.377839] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) c8:60:00:cc:af:e0
[    1.377840] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.377868] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.437570] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.437583] ata7: SATA link down (SStatus 0 SControl 300)
[    1.437607] ata9: SATA link down (SStatus 0 SControl 300)
[    1.440504] ata6.00: ATAPI: HL-DT-ST DVDRAM GSA-H66N, CB00, max UDMA/100
[    1.444787] ata6.00: configured for UDMA/100
[    1.453729] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H66N  CB00 PQ: 0 ANSI: 5
[    1.457898] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.457900] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.458001] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.458063] sr 5:0:0:0: Attached scsi generic sg0 type 5
[    1.517976] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.517978] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.518120] hub 2-1:1.0: USB hub found
[    1.518225] hub 2-1:1.0: 8 ports detected
[    1.589791] usb 1-1.6: new full-speed USB device number 3 using ehci-pci
[    1.682766] usb 1-1.6: New USB device found, idVendor=0b05, idProduct=179c
[    1.682768] usb 1-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.689750] tsc: Refined TSC clocksource calibration: 3699.949 MHz
[    1.789962] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    1.887442] usb 2-1.2: New USB device found, idVendor=045e, idProduct=0745
[    1.887444] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.887445] usb 2-1.2: Product: Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0
[    1.887447] usb 2-1.2: Manufacturer: Microsoft
[    1.889491] hidraw: raw HID events driver (C) Jiri Kosina
[    1.902680] usbcore: registered new interface driver usbhid
[    1.902681] usbhid: USB HID core driver
[    1.903633] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    1.903972] hid-generic 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:1d.0-1.2/input0
[    1.904186] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[    1.904264] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:1d.0-1.2/input1
[    1.914140] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input7
[    1.914227] hid-generic 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:1d.0-1.2/input2
[    1.949985] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.999883] ata8.00: ATA-9: ST1000DX001-1CM162, CC43, max UDMA/133
[    1.999885] ata8.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.033256] ata8.00: configured for UDMA/133
[    2.033355] scsi 7:0:0:0: Direct-Access     ATA      ST1000DX001-1CM1 CC43 PQ: 0 ANSI: 5
[    2.033448] sd 7:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.033449] sd 7:0:0:0: Attached scsi generic sg1 type 0
[    2.033451] sd 7:0:0:0: [sda] 4096-byte physical blocks
[    2.033533] sd 7:0:0:0: [sda] Write Protect is off
[    2.033535] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.033561] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.034368]  sda: sda1 sda2 sda3
[    2.034567] sd 7:0:0:0: [sda] Attached SCSI disk
[    2.350337] ata10: SATA link down (SStatus 0 SControl 300)
[    2.458423] nouveau  [  PTHERM][0000:04:00.0] FAN control: PWM
[    2.458436] nouveau  [  PTHERM][0000:04:00.0] fan management: automatic
[    2.458439] nouveau  [  PTHERM][0000:04:00.0] internal sensor: yes
[    2.458462] nouveau  [     CLK][0000:04:00.0] 03: core 50 MHz memory 135 MHz 
[    2.458464] nouveau  [     CLK][0000:04:00.0] 07: core 405 MHz memory 324 MHz 
[    2.458465] nouveau  [     CLK][0000:04:00.0] 0f: core 700 MHz memory 800 MHz 
[    2.458602] nouveau  [     CLK][0000:04:00.0] --: core 405 MHz memory 324 MHz 
[    2.462998] [TTM] Zone  kernel: Available graphics memory: 16443156 kiB
[    2.462999] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    2.462999] [TTM] Initializing pool allocator
[    2.463002] [TTM] Initializing DMA pool allocator
[    2.463006] nouveau  [     DRM] VRAM: 512 MiB
[    2.463006] nouveau  [     DRM] GART: 1048576 MiB
[    2.463009] nouveau  [     DRM] TMDS table version 2.0
[    2.463010] nouveau  [     DRM] DCB version 4.0
[    2.463011] nouveau  [     DRM] DCB outp 00: 01000302 00020030
[    2.463012] nouveau  [     DRM] DCB outp 01: 02000300 00000000
[    2.463013] nouveau  [     DRM] DCB outp 02: 08011392 00020020
[    2.463014] nouveau  [     DRM] DCB outp 03: 04022310 00000000
[    2.463015] nouveau  [     DRM] DCB conn 00: 00001030
[    2.463016] nouveau  [     DRM] DCB conn 01: 00002161
[    2.463017] nouveau  [     DRM] DCB conn 02: 00000200
[    2.463618] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.463619] [drm] No driver support for vblank timestamp query.
[    2.470713] nouveau  [     DRM] MM: using COPY0 for buffer copies
[    2.593110] nouveau  [     DRM] allocated 1920x1080 fb: 0x60000, bo ffff8807ecbe4400
[    2.593159] fbcon: nouveaufb (fb0) is primary device
[    2.655459] Console: switching to colour frame buffer device 240x67
[    2.657425] nouveau 0000:04:00.0: fb0: nouveaufb frame buffer device
[    2.657426] nouveau 0000:04:00.0: registered panic notifier
[    2.657429] [drm] Initialized nouveau 1.1.1 20120801 for 0000:04:00.0 on minor 0
[    2.690662] Switched to clocksource tsc
[    3.024831] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.315820] random: init urandom read with 116 bits of entropy available
[    5.750220] random: nonblocking pool is initialized
[   12.162267] Adding 29296636k swap on /dev/sda2.  Priority:-1 extents:1 across:29296636k FS
[   12.196155] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.228527] systemd-udevd[375]: starting version 204
[   12.277359] lp: driver loaded but no devices found
[   12.280254] ppdev: user-space parallel port driver
[   12.656707] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20131115/utaddress-251)
[   12.656713] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.656715] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20131115/utaddress-251)
[   12.656717] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.656718] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.664804] Bluetooth: Core ver 2.17
[   12.664820] NET: Registered protocol family 31
[   12.664821] Bluetooth: HCI device and connection manager initialized
[   12.664827] Bluetooth: HCI socket layer initialized
[   12.664829] Bluetooth: L2CAP socket layer initialized
[   12.664832] Bluetooth: SCO socket layer initialized
[   12.665932] EDAC MC: Ver: 3.0.0
[   12.666927] usbcore: registered new interface driver btusb
[   12.700323] snd_hda_intel 0000:00:1b.0: irq 101 for MSI/MSI-X
[   12.714448] SKU: Nid=0x1d sku_cfg=0x4007e629
[   12.714452] SKU: port_connectivity=0x1
[   12.714452] SKU: enable_pcbeep=0x0
[   12.714452] SKU: check_sum=0x00000007
[   12.714453] SKU: customization=0x000000e6
[   12.714453] SKU: external_amp=0x5
[   12.714453] SKU: platform_type=0x0
[   12.714453] SKU: swap=0x0
[   12.714453] SKU: override=0x1
[   12.714861] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[   12.714862]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.714862]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   12.714863]    mono: mono_out=0x0
[   12.714863]    dig-out=0x11/0x1e
[   12.714864]    inputs:
[   12.714865]      Front Mic=0x19
[   12.714866]      Rear Mic=0x18
[   12.714866]      Line=0x1a
[   12.714867] realtek: No valid SSID, checking pincfg 0x4007e629 for NID 0x1d
[   12.714867] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0899
[   12.725781] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   12.725817] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   12.725844] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   12.725872] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.725896] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.725923] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.725947] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.726107] hda_intel: Disabling MSI
[   12.726114] hda-intel 0000:04:00.1: Handle VGA-switcheroo audio client
[   12.726140] hda-intel 0000:04:00.1: Disabling 64bit DMA
[   12.729384] hda-intel 0000:04:00.1: Enable delay in RIRB handling
[   12.761443] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[   12.761447] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[   12.761449] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[   12.761452] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[   12.761453] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[   12.761456] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[   12.761457] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[   12.761459] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[   12.761461] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[   12.761463] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[   12.761464] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[   12.761467] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[   12.761468] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[   12.761471] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[   12.761472] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[   12.761475] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[   12.761476] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[   12.761479] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[   12.761479] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[   12.761482] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[   12.761483] EDAC sbridge: Seeking for: dev 1c.0 PCI ID 8086:0e60
[   12.761485] EDAC sbridge: Seeking for: dev 1d.2 PCI ID 8086:0e6a
[   12.761488] EDAC sbridge: Seeking for: dev 1d.3 PCI ID 8086:0e6b
[   12.761490] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:0eb8
[   12.761492] EDAC sbridge: Seeking for: dev 11.4 PCI ID 8086:0ebc
[   12.761494] EDAC sbridge: ECC is disabled. Aborting
[   12.761495] EDAC sbridge: Couldn't find mci handler
[   12.879259] mei_me 0000:00:16.0: irq 102 for MSI/MSI-X
[   12.897150] media: module verification failed: signature and/or  required key missing - tainting kernel
[   12.897304] media: Linux media interface: v0.10
[   12.897931] videodev: module has bad taint, not creating trace events
[   12.897956] Linux video capture interface: v2.00
[   12.897957] WARNING: You are using an experimental version of the media stack.
[   12.897957]     As the driver is backported to an older kernel, it doesn't offer
[   12.897957]     enough quality for its usage in production.
[   12.897957]     Use it with care.
[   12.897957] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   12.897957]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[   12.897957]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   12.897957]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[   12.913015] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.915649] type=1400 audit(1403386452.329:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=525 comm="apparmor_parser"
[   12.915654] type=1400 audit(1403386452.329:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=525 comm="apparmor_parser"
[   12.915657] type=1400 audit(1403386452.329:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=525 comm="apparmor_parser"
[   12.915941] type=1400 audit(1403386452.329:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=525 comm="apparmor_parser"
[   12.915945] type=1400 audit(1403386452.329:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=525 comm="apparmor_parser"
[   12.916093] type=1400 audit(1403386452.329:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=525 comm="apparmor_parser"
[   12.917409] type=1400 audit(1403386452.329:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=526 comm="apparmor_parser"
[   12.917414] type=1400 audit(1403386452.329:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
[   12.917417] type=1400 audit(1403386452.329:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=526 comm="apparmor_parser"
[   12.917712] type=1400 audit(1403386452.329:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=526 comm="apparmor_parser"
[   12.920584] asus_wmi: ASUS WMI generic driver loaded
[   12.921901] asus_wmi: Initialization: 0x0
[   12.921912] asus_wmi: BIOS WMI version: 0.9
[   12.921931] asus_wmi: SFUN value: 0x0
[   12.922077] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input15
[   12.922858] asus_wmi: Disabling ACPI video driver
[   13.012984] WARNING: You are using an experimental version of the media stack.
[   13.012984]     As the driver is backported to an older kernel, it doesn't offer
[   13.012984]     enough quality for its usage in production.
[   13.012984]     Use it with care.
[   13.012984] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   13.012984]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[   13.012984]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   13.012984]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[   13.039580] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   13.064788] WARNING: You are using an experimental version of the media stack.
[   13.064788]     As the driver is backported to an older kernel, it doesn't offer
[   13.064788]     enough quality for its usage in production.
[   13.064788]     Use it with care.
[   13.064788] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[   13.064788]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[   13.064788]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   13.064788]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[   13.268540] cx23885 driver version 0.0.3 loaded
[   13.268734] CORE cx23885[0]: subsystem: 0070:c108, board: Hauppauge WinTV-HVR4400 [card=38,autodetected]
[   13.294566] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   13.468030] init: failsafe main process (704) killed by TERM signal
[   13.511518] FS-Cache: Loaded
[   13.534450] RPC: Registered named UNIX socket transport module.
[   13.534451] RPC: Registered udp transport module.
[   13.534452] RPC: Registered tcp transport module.
[   13.534452] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   13.594561] tveeprom 12-0050: Hauppauge model 121019, rev B2F5, serial# 8647267
[   13.594563] tveeprom 12-0050: MAC address is 00:0d:fe:83:f2:63
[   13.594564] tveeprom 12-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[   13.594565] tveeprom 12-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   13.594566] tveeprom 12-0050: audio processor is CX23888 (idx 40)
[   13.594566] tveeprom 12-0050: decoder processor is CX23888 (idx 34)
[   13.594567] tveeprom 12-0050: has radio, has IR receiver, has no IR transmitter
[   13.594568] cx23885[0]: warning: unknown hauppauge model #121019
[   13.594569] cx23885[0]: hauppauge eeprom: model=121019
[   13.594570] cx23885_dvb_register() allocating 1 frontend(s)
[   13.594571] cx23885[0]: cx23885 based dvb card
[   13.610984] i2c i2c-12: a8293: Allegro A8293 SEC attached
[   13.610986] DVB: registering new adapter (cx23885[0])
[   13.610989] cx23885 0000:06:00.0: DVB: registering adapter 0 frontend 0 (NXP TDA10071)...
[   13.611114] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   13.611118] cx23885[0]/0: found at 0000:06:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfb200000
[   13.675986] FS-Cache: Netfs 'nfs' registered for caching
[   13.780523] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   13.833996] Bluetooth: RFCOMM TTY layer initialized
[   13.834006] Bluetooth: RFCOMM socket layer initialized
[   13.834010] Bluetooth: RFCOMM ver 1.11
[   13.863548] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.863550] Bluetooth: BNEP filters: protocol multicast
[   13.863557] Bluetooth: BNEP socket layer initialized
[   13.879605] init: cups main process (914) killed by HUP signal
[   13.879611] init: cups main process ended, respawning
[   14.169147] init: nvidia-prime main process (1026) terminated with status 127
[   14.174233] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   14.175417] zram: Created 8 device(s) ...
[   14.180918] Adding 2055392k swap on /dev/zram0.  Priority:5 extents:1 across:2055392k SSFS
[   14.183279] Adding 2055392k swap on /dev/zram1.  Priority:5 extents:1 across:2055392k SSFS
[   14.185520] Adding 2055392k swap on /dev/zram2.  Priority:5 extents:1 across:2055392k SSFS
[   14.187637] Adding 2055392k swap on /dev/zram3.  Priority:5 extents:1 across:2055392k SSFS
[   14.189761] Adding 2055392k swap on /dev/zram4.  Priority:5 extents:1 across:2055392k SSFS
[   14.191945] Adding 2055392k swap on /dev/zram5.  Priority:5 extents:1 across:2055392k SSFS
[   14.194990] Adding 2055392k swap on /dev/zram6.  Priority:5 extents:1 across:2055392k SSFS
[   14.197107] Adding 2055392k swap on /dev/zram7.  Priority:5 extents:1 across:2055392k SSFS
[   14.232311] init: tftpd-hpa main process (1103) terminated with status 66
[   14.232318] init: tftpd-hpa main process ended, respawning
[   14.300688] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input19
[   14.300733] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input18
[   14.300764] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input17
[   14.300793] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input16
[   14.354479] init: isc-dhcp-server main process (1098) terminated with status 1
[   14.354489] init: isc-dhcp-server main process ended, respawning
[   14.423933] init: mythbuntu-bare-console main process (1297) terminated with status 1
[   14.423942] init: mythbuntu-bare-console main process ended, respawning
[   14.426858] init: mythbuntu-bare-console-processor main process (1301) terminated with status 1
[   14.426866] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.472675] init: samba-ad-dc main process (1005) terminated with status 1
[   14.483039] init: mythbuntu-bare-console main process (1388) terminated with status 1
[   14.483047] init: mythbuntu-bare-console main process ended, respawning
[   14.495753] init: mythbuntu-bare-console-processor main process (1390) terminated with status 1
[   14.495766] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.501546] init: isc-dhcp-server main process (1333) terminated with status 1
[   14.501553] init: isc-dhcp-server main process ended, respawning
[   14.553489] init: mythbuntu-bare-console main process (1393) terminated with status 1
[   14.553498] init: mythbuntu-bare-console main process ended, respawning
[   14.569042] init: mythbuntu-bare-console-processor main process (1395) terminated with status 1
[   14.569051] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.610436] init: mythbuntu-bare-console main process (1426) terminated with status 1
[   14.610447] init: mythbuntu-bare-console main process ended, respawning
[   14.636754] init: mythbuntu-bare-console-processor main process (1430) terminated with status 1
[   14.636763] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.676622] init: mythbuntu-bare-console main process (1440) terminated with status 1
[   14.676630] init: mythbuntu-bare-console main process ended, respawning
[   14.678029] e1000e 0000:00:19.0: irq 98 for MSI/MSI-X
[   14.704840] init: mythbuntu-bare-console-processor main process (1445) terminated with status 1
[   14.704850] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.734096] init: mythbuntu-bare-console main process (1448) terminated with status 1
[   14.734104] init: mythbuntu-bare-console main process ended, respawning
[   14.773728] init: mythbuntu-bare-console-processor main process (1455) terminated with status 1
[   14.773742] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.781091] e1000e 0000:00:19.0: irq 98 for MSI/MSI-X
[   14.781186] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.781363] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.783648] init: isc-dhcp-server main process (1410) terminated with status 1
[   14.783659] init: isc-dhcp-server main process ended, respawning
[   14.796439] init: mythbuntu-bare-console main process (1473) terminated with status 1
[   14.796446] init: mythbuntu-bare-console main process ended, respawning
[   14.843894] init: mythbuntu-bare-console-processor main process (1502) terminated with status 1
[   14.843907] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.854341] init: mythbuntu-bare-console main process (1512) terminated with status 1
[   14.854354] init: mythbuntu-bare-console main process ended, respawning
[   14.873198] init: isc-dhcp-server main process (1506) terminated with status 1
[   14.873211] init: isc-dhcp-server main process ended, respawning
[   14.902494] init: isc-dhcp-server main process (1536) terminated with status 1
[   14.902505] init: isc-dhcp-server main process ended, respawning
[   14.918140] init: mythbuntu-bare-console main process (1532) terminated with status 1
[   14.918152] init: mythbuntu-bare-console main process ended, respawning
[   14.926035] init: mythbuntu-bare-console-processor main process (1528) terminated with status 1
[   14.926044] init: mythbuntu-bare-console-processor main process ended, respawning
[   14.975099] init: mythbuntu-bare-console main process (1550) terminated with status 1
[   14.975108] init: mythbuntu-bare-console main process ended, respawning
[   14.991409] init: isc-dhcp-server main process (1544) terminated with status 1
[   14.991417] init: isc-dhcp-server main process ended, respawning
[   14.995133] init: mythbuntu-bare-console-processor main process (1552) terminated with status 1
[   14.995148] init: mythbuntu-bare-console-processor main process ended, respawning
[   15.030118] init: isc-dhcp-server main process (1560) terminated with status 1
[   15.030128] init: isc-dhcp-server main process ended, respawning
[   15.037071] init: mythbuntu-bare-console main process (1554) terminated with status 1
[   15.037082] init: mythbuntu-bare-console respawning too fast, stopped
[   15.044687] init: mythbuntu-bare-console-processor main process (1558) killed by TERM signal
[   15.065340] init: isc-dhcp-server main process (1570) terminated with status 1
[   15.065348] init: isc-dhcp-server main process ended, respawning
[   15.092278] init: isc-dhcp-server main process (1584) terminated with status 1
[   15.092286] init: isc-dhcp-server main process ended, respawning
[   15.121673] init: isc-dhcp-server main process (1594) terminated with status 1
[   15.121681] init: isc-dhcp-server main process ended, respawning
[   15.124147] init: plymouth-upstart-bridge main process ended, respawning
[   15.131742] init: plexmediaserver main process (1023) terminated with status 255
[   15.131750] init: plexmediaserver main process ended, respawning
[   15.131900] init: plymouth-upstart-bridge main process (1606) terminated with status 1
[   15.131907] init: plymouth-upstart-bridge main process ended, respawning
[   15.167579] init: isc-dhcp-server main process (1608) terminated with status 1
[   15.167587] init: isc-dhcp-server respawning too fast, stopped
[   16.639470] init: plymouth-stop pre-start process (1985) terminated with status 1
[   18.341052] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   18.341084] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   43.947590] audit_printk_skb: 195 callbacks suppressed
[   43.947592] type=1400 audit(1403386483.326:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3043 comm="apparmor_parser"
[   43.947596] type=1400 audit(1403386483.326:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3043 comm="apparmor_parser"
[   43.947816] type=1400 audit(1403386483.326:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3043 comm="apparmor_parser"

```

found this:

```

[   12.761492] EDAC sbridge: Seeking for: dev 11.4 PCI ID 8086:0ebc
[   12.761494] EDAC sbridge: ECC is disabled. Aborting
[   12.761495] EDAC sbridge: Couldn't find mci handler
[   12.879259] mei_me 0000:00:16.0: irq 102 for MSI/MSI-X
[   12.897150] media: module verification failed: signature and/or  required key missing - tainting kernel
[   12.897304] media: Linux media interface: v0.10
[   12.897931] videodev: module has bad taint, not creating trace events
[   12.897956] Linux video capture interface: v2.00
[   12.897957] WARNING: You are using an experimental version of the media stack.
[   12.897957]     As the driver is backported to an older kernel, it doesn't offer
[   12.897957]     enough quality for its usage in production.
[   12.897957]     Use it with care.
[   12.897957] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[    12.897957]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2:  soc_camera: Add run-time dependencies to sh_mobile drivers
[   12.897957]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[   12.897957]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[   12.913015] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
```

and this..

```

[   13.534450] RPC: Registered named UNIX socket transport module.
[   13.534451] RPC: Registered udp transport module.
[   13.534452] RPC: Registered tcp transport module.
[   13.534452] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   13.594561] tveeprom 12-0050: Hauppauge model 121019, rev B2F5, serial# 8647267
[   13.594563] tveeprom 12-0050: MAC address is 00:0d:fe:83:f2:63
[   13.594564] tveeprom 12-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[   13.594565] tveeprom 12-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[   13.594566] tveeprom 12-0050: audio processor is CX23888 (idx 40)
[   13.594566] tveeprom 12-0050: decoder processor is CX23888 (idx 34)
[   13.594567] tveeprom 12-0050: has radio, has IR receiver, has no IR transmitter
[   13.594568] cx23885[0]: warning: unknown hauppauge model #121019
[   13.594569] cx23885[0]: hauppauge eeprom: model=121019
[   13.594570] cx23885_dvb_register() allocating 1 frontend(s)
[   13.594571] cx23885[0]: cx23885 based dvb card
[   13.610984] i2c i2c-12: a8293: Allegro A8293 SEC attached
[   13.610986] DVB: registering new adapter (cx23885[0])
[   13.610989] cx23885 0000:06:00.0: DVB: registering adapter 0 frontend 0 (NXP TDA10071)...
[   13.611114] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   13.611118] cx23885[0]/0: found at 0000:06:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfb200000
[   13.675986] FS-Cache: Netfs 'nfs' registered for caching
[   13.780523] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).

```

---

### Post by xc3RnbFO8P on 2014-06-22
Check if you have this driver **dvb-fe-tda10071.fw** in /lib/firmware

---

### Post by jonathan-l-harrison on 2014-06-22
no.  don't have it

---

### Post by xc3RnbFO8P on 2014-06-22
Copy&paste this in gedit and save it (any name you want) in your home folder
open terminal and type: sudo perl /path to your file

restart and do **dmesg**

```
#!/usr/bin/perl
#     DVB firmware extractor
#
#     (c) 2004 Andrew de Quincey
#
#     This program is free software; you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation; either version 2 of the License, or
#       (at your option) any later version.
#
#     This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#
#     GNU General Public License for more details.
#
#     You should have received a copy of the GNU General Public License
#       along with this program; if not, write to the Free Software
#       Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

use File::Temp qw/ tempdir /;
use IO::Handle;

@components = ( "sp8870", "sp887x", "tda10045", "tda10046",
		"tda10046lifeview", "av7110", "dec2000t", "dec2540t",
		"dec3000s", "vp7041", "vp7049", "dibusb", "nxt2002", "nxt2004",
		"or51211", "or51132_qam", "or51132_vsb", "bluebird",
		"opera1", "cx231xx", "cx18", "cx23885", "pvrusb2", "mpc718",
		"af9015", "ngene", "az6027", "lme2510_lg", "lme2510c_s7395",
		"lme2510c_s7395_old", "drxk", "drxk_terratec_h5",
		"drxk_hauppauge_hvr930c", "tda10071", "it9135", "drxk_pctv",
		"drxk_terratec_htc_stick", "sms1xxx_hcw");

# Check args
syntax() if (scalar(@ARGV) != 1);
$cid = $ARGV[0];

# Do it!
for ($i=0; $i < scalar(@components); $i++) {
    if ($cid eq $components[$i]) {
	$outfile = eval($cid);
	die $@ if $@;
	print STDERR <<EOF;
Firmware(s) $outfile extracted successfully.
Now copy it(them) to either /usr/lib/hotplug/firmware or /lib/firmware
(depending on configuration of firmware hotplug).
EOF
	exit(0);
    }
}

# If we get here, it wasn't found
print STDERR "Unknown component \"$cid\"\n";
syntax();




# ---------------------------------------------------------------
# Firmware-specific extraction subroutines

sub sp8870 {
    my $sourcefile = "tt_Premium_217g.zip";
    my $url = "http://www.softwarepatch.pl/9999ccd06a4813cb827dbb0005071c71/$sourcefile";
    my $hash = "53970ec17a538945a6d8cb608a7b3899";
    my $outfile = "dvb-fe-sp8870.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    verify("$tmpdir/software/OEM/HE/App/boot/SC_MAIN.MC", $hash);
    copy("$tmpdir/software/OEM/HE/App/boot/SC_MAIN.MC", $outfile);

    $outfile;
}

sub sp887x {
    my $sourcefile = "Dvbt1.3.57.6.zip";
    my $url = "http://www.avermedia.com/software/$sourcefile";
    my $cabfile = "DVBT Net  Ver1.3.57.6/disk1/data1.cab";
    my $hash = "237938d53a7f834c05c42b894ca68ac3";
    my $outfile = "dvb-fe-sp887x.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();
    checkunshield();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    unshield("$tmpdir/$cabfile", $tmpdir);
    verify("$tmpdir/ZEnglish/sc_main.mc", $hash);
    copy("$tmpdir/ZEnglish/sc_main.mc", $outfile);

    $outfile;
}

sub tda10045 {
    my $sourcefile = "tt_budget_217g.zip";
    my $url = "http://www.technotrend.de/new/217g/$sourcefile";
    my $hash = "2105fd5bf37842fbcdfa4bfd58f3594a";
    my $outfile = "dvb-fe-tda10045.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    extract("$tmpdir/software/OEM/PCI/App/ttlcdacc.dll", 0x37ef9, 30555, "$tmpdir/fwtmp");
    verify("$tmpdir/fwtmp", $hash);
    copy("$tmpdir/fwtmp", $outfile);

    $outfile;
}

sub tda10046 {
	my $sourcefile = "TT_PCI_2.19h_28_11_2006.zip";
	my $url = "http://technotrend.com.ua/download/software/219/$sourcefile";
	my $hash = "6a7e1e2f2644b162ff0502367553c72d";
	my $outfile = "dvb-fe-tda10046.fw";
	my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

	checkstandard();

	wgetfile($sourcefile, $url);
	unzip($sourcefile, $tmpdir);
	extract("$tmpdir/TT_PCI_2.19h_28_11_2006/software/OEM/PCI/App/ttlcdacc.dll", 0x65389, 24478, "$tmpdir/fwtmp");
	verify("$tmpdir/fwtmp", $hash);
	copy("$tmpdir/fwtmp", $outfile);

	$outfile;
}

sub tda10046lifeview {
    my $sourcefile = "7%5Cdrv_2.11.02.zip";
    my $url = "http://www.lifeview.hk/dbimages/document/$sourcefile";
    my $hash = "1ea24dee4eea8fe971686981f34fd2e0";
    my $outfile = "dvb-fe-tda10046.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    extract("$tmpdir/LVHybrid.sys", 0x8b088, 24602, "$tmpdir/fwtmp");
    verify("$tmpdir/fwtmp", $hash);
    copy("$tmpdir/fwtmp", $outfile);

    $outfile;
}

sub av7110 {
    my $sourcefile = "dvb-ttpci-01.fw-261d";
    my $url = "http://www.linuxtv.org/downloads/firmware/$sourcefile";
    my $hash = "603431b6259715a8e88f376a53b64e2f";
    my $outfile = "dvb-ttpci-01.fw";

    checkstandard();

    wgetfile($sourcefile, $url);
    verify($sourcefile, $hash);
    copy($sourcefile, $outfile);

    $outfile;
}

sub dec2000t {
    my $sourcefile = "dec217g.exe";
    my $url = "http://hauppauge.lightpath.net/de/$sourcefile";
    my $hash = "bd86f458cee4a8f0a8ce2d20c66215a9";
    my $outfile = "dvb-ttusb-dec-2000t.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    verify("$tmpdir/software/OEM/STB/App/Boot/STB_PC_T.bin", $hash);
    copy("$tmpdir/software/OEM/STB/App/Boot/STB_PC_T.bin", $outfile);

    $outfile;
}

sub dec2540t {
    my $sourcefile = "dec217g.exe";
    my $url = "http://hauppauge.lightpath.net/de/$sourcefile";
    my $hash = "53e58f4f5b5c2930beee74a7681fed92";
    my $outfile = "dvb-ttusb-dec-2540t.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    verify("$tmpdir/software/OEM/STB/App/Boot/STB_PC_X.bin", $hash);
    copy("$tmpdir/software/OEM/STB/App/Boot/STB_PC_X.bin", $outfile);

    $outfile;
}

sub dec3000s {
    my $sourcefile = "dec217g.exe";
    my $url = "http://hauppauge.lightpath.net/de/$sourcefile";
    my $hash = "b013ececea83f4d6d8d2a29ac7c1b448";
    my $outfile = "dvb-ttusb-dec-3000s.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    verify("$tmpdir/software/OEM/STB/App/Boot/STB_PC_S.bin", $hash);
    copy("$tmpdir/software/OEM/STB/App/Boot/STB_PC_S.bin", $outfile);

    $outfile;
}
sub opera1{
	my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 0);

	checkstandard();
	my $fwfile1="dvb-usb-opera1-fpga-01.fw";
	my $fwfile2="dvb-usb-opera-01.fw";
	extract("2830SCap2.sys", 0x62e8, 55024, "$tmpdir/opera1-fpga.fw");
	extract("2830SLoad2.sys",0x3178,0x3685-0x3178,"$tmpdir/fw1part1");
	extract("2830SLoad2.sys",0x0980,0x3150-0x0980,"$tmpdir/fw1part2");
	delzero("$tmpdir/fw1part1","$tmpdir/fw1part1-1");
	delzero("$tmpdir/fw1part2","$tmpdir/fw1part2-1");
	verify("$tmpdir/fw1part1-1","5e0909858fdf0b5b09ad48b9fe622e70");
	verify("$tmpdir/fw1part2-1","d6e146f321427e931df2c6fcadac37a1");
	verify("$tmpdir/opera1-fpga.fw","0f8133f5e9051f5f3c1928f7e5a1b07d");

	my $RES1="\x01\x92\x7f\x00\x01\x00";
	my $RES0="\x01\x92\x7f\x00\x00\x00";
	my $DAT1="\x01\x00\xe6\x00\x01\x00";
	my $DAT0="\x01\x00\xe6\x00\x00\x00";
	open FW,">$tmpdir/opera.fw";
	print FW "$RES1";
	print FW "$DAT1";
	print FW "$RES1";
	print FW "$DAT1";
	appendfile(FW,"$tmpdir/fw1part1-1");
	print FW "$RES0";
	print FW "$DAT0";
	print FW "$RES1";
	print FW "$DAT1";
	appendfile(FW,"$tmpdir/fw1part2-1");
	print FW "$RES1";
	print FW "$DAT1";
	print FW "$RES0";
	print FW "$DAT0";
	copy ("$tmpdir/opera1-fpga.fw",$fwfile1);
	copy ("$tmpdir/opera.fw",$fwfile2);

	$fwfile1.",".$fwfile2;
}

sub vp7041 {
    my $sourcefile = "2.422.zip";
    my $url = "http://www.twinhan.com/files/driver/USB-Ter/$sourcefile";
    my $hash = "e88c9372d1f66609a3e7b072c53fbcfe";
    my $outfile = "dvb-vp7041-2.422.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    extract("$tmpdir/VisionDTV/Drivers/Win2K&XP/UDTTload.sys", 12503, 3036, "$tmpdir/fwtmp1");
    extract("$tmpdir/VisionDTV/Drivers/Win2K&XP/UDTTload.sys", 2207, 10274, "$tmpdir/fwtmp2");

    my $CMD = "\000\001\000\222\177\000";
    my $PAD = "\000\000\000\000\000\000\000\000\000\000\000\000\000\000\000";
    my ($FW);
    open $FW, ">$tmpdir/fwtmp3";
    print $FW "$CMD\001$PAD";
    print $FW "$CMD\001$PAD";
    appendfile($FW, "$tmpdir/fwtmp1");
    print $FW "$CMD\000$PAD";
    print $FW "$CMD\001$PAD";
    appendfile($FW, "$tmpdir/fwtmp2");
    print $FW "$CMD\001$PAD";
    print $FW "$CMD\000$PAD";
    close($FW);

    verify("$tmpdir/fwtmp3", $hash);
    copy("$tmpdir/fwtmp3", $outfile);

    $outfile;
}

sub vp7049 {
    my $fwfile = "dvb-usb-vp7049-0.95.fw";
    my $url = "http://ao2.it/sites/default/files/blog/2012/11/06/linux-support-digicom-digitune-s-vp7049-udtt7049/$fwfile";
    my $hash = "5609fd295168aea88b25ff43a6f79c36";

    checkstandard();

    wgetfile($fwfile, $url);
    verify($fwfile, $hash);

    $fwfile;
}

sub dibusb {
	my $url = "http://www.linuxtv.org/downloads/firmware/dvb-usb-dibusb-5.0.0.11.fw";
	my $outfile = "dvb-dibusb-5.0.0.11.fw";
	my $hash = "fa490295a527360ca16dcdf3224ca243";

	checkstandard();

	wgetfile($outfile, $url);
	verify($outfile,$hash);

	$outfile;
}

sub nxt2002 {
    my $sourcefile = "Technisat_DVB-PC_4_4_COMPACT.zip";
    my $url = "http://www.bbti.us/download/windows/$sourcefile";
    my $hash = "476befae8c7c1bb9648954060b1eec1f";
    my $outfile = "dvb-fe-nxt2002.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    verify("$tmpdir/SkyNET.sys", $hash);
    extract("$tmpdir/SkyNET.sys", 331624, 5908, $outfile);

    $outfile;
}

sub nxt2004 {
    my $sourcefile = "AVerTVHD_MCE_A180_Drv_v1.2.2.16.zip";
    my $url = "http://www.avermedia-usa.com/support/Drivers/$sourcefile";
    my $hash = "111cb885b1e009188346d72acfed024c";
    my $outfile = "dvb-fe-nxt2004.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url);
    unzip($sourcefile, $tmpdir);
    verify("$tmpdir/3xHybrid.sys", $hash);
    extract("$tmpdir/3xHybrid.sys", 465304, 9584, $outfile);

    $outfile;
}

sub or51211 {
    my $fwfile = "dvb-fe-or51211.fw";
    my $url = "http://linuxtv.org/downloads/firmware/$fwfile";
    my $hash = "d830949c771a289505bf9eafc225d491";

    checkstandard();

    wgetfile($fwfile, $url);
    verify($fwfile, $hash);

    $fwfile;
}

sub cx231xx {
    my $fwfile = "v4l-cx231xx-avcore-01.fw";
    my $url = "http://linuxtv.org/downloads/firmware/$fwfile";
    my $hash = "7d3bb956dc9df0eafded2b56ba57cc42";

    checkstandard();

    wgetfile($fwfile, $url);
    verify($fwfile, $hash);

    $fwfile;
}

sub cx18 {
    my $url = "http://linuxtv.org/downloads/firmware/";

    my %files = (
	'v4l-cx23418-apu.fw' => '588f081b562f5c653a3db1ad8f65939a',
	'v4l-cx23418-cpu.fw' => 'b6c7ed64bc44b1a6e0840adaeac39d79',
	'v4l-cx23418-dig.fw' => '95bc688d3e7599fd5800161e9971cc55',
    );

    checkstandard();

    my $allfiles;
    foreach my $fwfile (keys %files) {
	wgetfile($fwfile, "$url/$fwfile");
	verify($fwfile, $files{$fwfile});
	$allfiles .= " $fwfile";
    }

    $allfiles =~ s/^\s//;

    $allfiles;
}

sub mpc718 {
    my $archive = 'Yuan MPC718 TV Tuner Card 2.13.10.1016.zip';
    my $url = "ftp://ftp.work.acer-euro.com/desktop/aspire_idea510/vista/Drivers/$archive";
    my $fwfile = "dvb-cx18-mpc718-mt352.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();
    wgetfile($archive, $url);
    unzip($archive, $tmpdir);

    my $sourcefile = "$tmpdir/Yuan MPC718 TV Tuner Card 2.13.10.1016/mpc718_32bit/yuanrap.sys";
    my $found = 0;

    open IN, '<', $sourcefile or die "Couldn't open $sourcefile to extract $fwfile data\n";
    binmode IN;
    open OUT, '>', $fwfile;
    binmode OUT;
    {
	# Block scope because we change the line terminator variable $/
	my $prevlen = 0;
	my $currlen;

	# Buried in the data segment are 3 runs of almost identical
	# register-value pairs that end in 0x5d 0x01 which is a "TUNER GO"
	# command for the MT352.
	# Pull out the middle run (because it's easy) of register-value
	# pairs to make the "firmware" file.

	local $/ = "\x5d\x01"; # MT352 "TUNER GO"

	while (<IN>) {
	    $currlen = length($_);
	    if ($prevlen == $currlen && $currlen <= 64) {
		chop; chop; # Get rid of "TUNER GO"
		s/^\0\0//;  # get rid of leading 00 00 if it's there
		printf OUT "$_";
		$found = 1;
		last;
	    }
	    $prevlen = $currlen;
	}
    }
    close OUT;
    close IN;
    if (!$found) {
	unlink $fwfile;
	die "Couldn't find valid register-value sequence in $sourcefile for $fwfile\n";
    }
    $fwfile;
}

sub cx23885 {
    my $url = "http://linuxtv.org/downloads/firmware/";

    my %files = (
	'v4l-cx23885-avcore-01.fw' => 'a9f8f5d901a7fb42f552e1ee6384f3bb',
	'v4l-cx23885-enc.fw'       => 'a9f8f5d901a7fb42f552e1ee6384f3bb',
    );

    checkstandard();

    my $allfiles;
    foreach my $fwfile (keys %files) {
	wgetfile($fwfile, "$url/$fwfile");
	verify($fwfile, $files{$fwfile});
	$allfiles .= " $fwfile";
    }

    $allfiles =~ s/^\s//;

    $allfiles;
}

sub pvrusb2 {
    my $url = "http://linuxtv.org/downloads/firmware/";

    my %files = (
	'v4l-cx25840.fw'           => 'dadb79e9904fc8af96e8111d9cb59320',
    );

    checkstandard();

    my $allfiles;
    foreach my $fwfile (keys %files) {
	wgetfile($fwfile, "$url/$fwfile");
	verify($fwfile, $files{$fwfile});
	$allfiles .= " $fwfile";
    }

    $allfiles =~ s/^\s//;

    $allfiles;
}

sub or51132_qam {
    my $fwfile = "dvb-fe-or51132-qam.fw";
    my $url = "http://linuxtv.org/downloads/firmware/$fwfile";
    my $hash = "7702e8938612de46ccadfe9b413cb3b5";

    checkstandard();

    wgetfile($fwfile, $url);
    verify($fwfile, $hash);

    $fwfile;
}

sub or51132_vsb {
    my $fwfile = "dvb-fe-or51132-vsb.fw";
    my $url = "http://linuxtv.org/downloads/firmware/$fwfile";
    my $hash = "c16208e02f36fc439a557ad4c613364a";

    checkstandard();

    wgetfile($fwfile, $url);
    verify($fwfile, $hash);

    $fwfile;
}

sub bluebird {
	my $url = "http://www.linuxtv.org/download/dvb/firmware/dvb-usb-bluebird-01.fw";
	my $outfile = "dvb-usb-bluebird-01.fw";
	my $hash = "658397cb9eba9101af9031302671f49d";

	checkstandard();

	wgetfile($outfile, $url);
	verify($outfile,$hash);

	$outfile;
}

sub af9015 {
	my $sourcefile = "download.ashx?file=57";
	my $url = "http://www.ite.com.tw/EN/Services/$sourcefile";
	my $hash = "e3f08935158038d385ad382442f4bb2d";
	my $outfile = "dvb-usb-af9015.fw";
	my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);
	my $fwoffset = 0x25690;
	my $fwlength = 18725;
	my ($chunklength, $buf, $rcount);

	checkstandard();

	wgetfile($sourcefile, $url);
	unzip($sourcefile, $tmpdir);
	verify("$tmpdir/Driver/Files/AF15BDA.sys", $hash);

	open INFILE, '<', "$tmpdir/Driver/Files/AF15BDA.sys";
	open OUTFILE, '>', $outfile;

	sysseek(INFILE, $fwoffset, SEEK_SET);
	while($fwlength > 0) {
		$chunklength = 55;
		$chunklength = $fwlength if ($chunklength > $fwlength);
		$rcount = sysread(INFILE, $buf, $chunklength);
		die "Ran out of data\n" if ($rcount != $chunklength);
		syswrite(OUTFILE, $buf);
		sysread(INFILE, $buf, 8);
		$fwlength -= $rcount + 8;
	}

	close OUTFILE;
	close INFILE;
}

sub ngene {
    my $url = "http://www.digitaldevices.de/download/";
    my $file1 = "ngene_15.fw";
    my $hash1 = "d798d5a757121174f0dbc5f2833c0c85";
    my $file2 = "ngene_17.fw";
    my $hash2 = "26b687136e127b8ac24b81e0eeafc20b";
    my $url2 = "http://l4m-daten.de/downloads/firmware/dvb-s2/linux/all/";
    my $file3 = "ngene_18.fw";
    my $hash3 = "ebce3ea769a53e3e0b0197c3b3f127e3";

    checkstandard();

    wgetfile($file1, $url . $file1);
    verify($file1, $hash1);

    wgetfile($file2, $url . $file2);
    verify($file2, $hash2);

    wgetfile($file3, $url2 . $file3);
    verify($file3, $hash3);

    "$file1, $file2, $file3";
}

sub az6027{
    my $firmware = "dvb-usb-az6027-03.fw";
    my $url = "http://linux.terratec.de/files/TERRATEC_S7/$firmware";

    wgetfile($firmware, $url);

    $firmware;
}

sub lme2510_lg {
    my $sourcefile = "LMEBDA_DVBS.sys";
    my $hash = "fc6017ad01e79890a97ec53bea157ed2";
    my $outfile = "dvb-usb-lme2510-lg.fw";
    my $hasho = "caa065d5fdbd2c09ad57b399bbf55cad";

    checkstandard();

    verify($sourcefile, $hash);
    extract($sourcefile, 4168, 3841, $outfile);
    verify($outfile, $hasho);
    $outfile;
}

sub lme2510c_s7395 {
    my $sourcefile = "US2A0D.sys";
    my $hash = "b0155a8083fb822a3bd47bc360e74601";
    my $outfile = "dvb-usb-lme2510c-s7395.fw";
    my $hasho = "3a3cf1aeebd17b6ddc04cebe131e94cf";

    checkstandard();

    verify($sourcefile, $hash);
    extract($sourcefile, 37248, 3720, $outfile);
    verify($outfile, $hasho);
    $outfile;
}

sub lme2510c_s7395_old {
    my $sourcefile = "LMEBDA_DVBS7395C.sys";
    my $hash = "7572ae0eb9cdf91baabd7c0ba9e09b31";
    my $outfile = "dvb-usb-lme2510c-s7395.fw";
    my $hasho = "90430c5b435eb5c6f88fd44a9d950674";

    checkstandard();

    verify($sourcefile, $hash);
    extract($sourcefile, 4208, 3881, $outfile);
    verify($outfile, $hasho);
    $outfile;
}

sub drxk {
    my $url = "http://l4m-daten.de/files/";
    my $zipfile = "DDTuner.zip";
    my $hash = "f5a37b9a20a3534997997c0b1382a3e5";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);
    my $drvfile = "DDTuner.sys";
    my $fwfile = "drxk_a3.mc";

    checkstandard();

    wgetfile($zipfile, $url . $zipfile);
    verify($zipfile, $hash);
    unzip($zipfile, $tmpdir);
    extract("$tmpdir/$drvfile", 0x14dd8, 15634, "$fwfile");

    "$fwfile"
}

sub drxk_hauppauge_hvr930c {
    my $url = "http://www.wintvcd.co.uk/drivers/";
    my $zipfile = "HVR-9x0_5_10_325_28153_SIGNED.zip";
    my $hash = "83ab82e7e9480ec8bf1ae0155ca63c88";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);
    my $drvfile = "HVR-900/emOEM.sys";
    my $fwfile = "dvb-usb-hauppauge-hvr930c-drxk.fw";

    checkstandard();

    wgetfile($zipfile, $url . $zipfile);
    verify($zipfile, $hash);
    unzip($zipfile, $tmpdir);
    extract("$tmpdir/$drvfile", 0x117b0, 42692, "$fwfile");

    "$fwfile"
}

sub drxk_terratec_h5 {
    my $url = "http://www.linuxtv.org/downloads/firmware/";
    my $hash = "19000dada8e2741162ccc50cc91fa7f1";
    my $fwfile = "dvb-usb-terratec-h5-drxk.fw";

    checkstandard();

    wgetfile($fwfile, $url . $fwfile);
    verify($fwfile, $hash);

    "$fwfile"
}

sub drxk_terratec_htc_stick {
    my $url = "http://ftp.terratec.de/Receiver/Cinergy_HTC_Stick/Updates/History/";
    my $zipfile = "Cinergy_HTC_Stick_Drv_5.09.1202.00_XP_Vista_7.exe";
    my $hash = "6722a2442a05423b781721fbc069ed5e";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 0);
    my $drvfile = "Cinergy HTC Stick/BDA Driver 5.09.1202.00/Windows 32 Bit/emOEM.sys";
    my $fwfile = "dvb-usb-terratec-htc-stick-drxk.fw";

    checkstandard();

    wgetfile($zipfile, $url . $zipfile);
    verify($zipfile, $hash);
    unzip($zipfile, $tmpdir);
    extract("$tmpdir/$drvfile", 0x4e5c0, 42692, "$fwfile");

    "$fwfile"
}

sub it9135 {
	my $sourcefile = "dvb-usb-it9135.zip";
	my $url = "http://www.ite.com.tw/uploads/firmware/v3.6.0.0/$sourcefile";
	my $hash = "1e55f6c8833f1d0ae067c2bb2953e6a9";
	my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 0);
	my $outfile = "dvb-usb-it9135.fw";
	my $fwfile1 = "dvb-usb-it9135-01.fw";
	my $fwfile2 = "dvb-usb-it9135-02.fw";

	checkstandard();

	wgetfile($sourcefile, $url);
	unzip($sourcefile, $tmpdir);
	verify("$tmpdir/$outfile", $hash);
	extract("$tmpdir/$outfile", 64, 8128, "$fwfile1");
	extract("$tmpdir/$outfile", 12866, 5817, "$fwfile2");

	"$fwfile1 $fwfile2"
}

sub tda10071 {
    my $sourcefile = "PCTV_460e_reference.zip";
    my $url = "ftp://ftp.pctvsystems.com/TV/driver/PCTV%2070e%2080e%20100e%20320e%20330e%20800e/";
    my $hash = "4403de903bf2593464c8d74bbc200a57";
    my $fwfile = "dvb-fe-tda10071.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url . $sourcefile);
    verify($sourcefile, $hash);
    unzip($sourcefile, $tmpdir);
    extract("$tmpdir/PCTV\ 70e\ 80e\ 100e\ 320e\ 330e\ 800e/32\ bit/emOEM.sys", 0x67d38, 40504, $fwfile);

    "$fwfile";
}

sub drxk_pctv {
    my $sourcefile = "PCTV_460e_reference.zip";
    my $url = "ftp://ftp.pctvsystems.com/TV/driver/PCTV%2070e%2080e%20100e%20320e%20330e%20800e/";
    my $hash = "4403de903bf2593464c8d74bbc200a57";
    my $fwfile = "dvb-demod-drxk-pctv.fw";
    my $tmpdir = tempdir(DIR => "/tmp", CLEANUP => 1);

    checkstandard();

    wgetfile($sourcefile, $url . $sourcefile);
    verify($sourcefile, $hash);
    unzip($sourcefile, $tmpdir);
    extract("$tmpdir/PCTV\ 70e\ 80e\ 100e\ 320e\ 330e\ 800e/32\ bit/emOEM.sys", 0x72b80, 42692, $fwfile);

    "$fwfile";
}

sub sms1xxx_hcw {
    my $url = "http://steventoth.net/linux/sms1xxx/";
    my %files = (
	'sms1xxx-hcw-55xxx-dvbt-01.fw'  => "afb6f9fb9a71d64392e8564ef9577e5a",
	'sms1xxx-hcw-55xxx-dvbt-02.fw'  => "b44807098ba26e52cbedeadc052ba58f",
	'sms1xxx-hcw-55xxx-isdbt-02.fw' => "dae934eeea85225acbd63ce6cfe1c9e4",
    );

    checkstandard();

    my $allfiles;
    foreach my $fwfile (keys %files) {
	wgetfile($fwfile, "$url/$fwfile");
	verify($fwfile, $files{$fwfile});
	$allfiles .= " $fwfile";
    }

    $allfiles =~ s/^\s//;

    $allfiles;
}

# ---------------------------------------------------------------
# Utilities

sub checkstandard {
    if (system("which unzip > /dev/null 2>&1")) {
	die "This firmware requires the unzip command - see ftp://ftp.info-zip.org/pub/infozip/UnZip.html\n";
    }
    if (system("which md5sum > /dev/null 2>&1")) {
	die "This firmware requires the md5sum command - see http://www.gnu.org/software/coreutils/\n";
    }
    if (system("which wget > /dev/null 2>&1")) {
	die "This firmware requires the wget command - see http://wget.sunsite.dk/\n";
    }
}

sub checkunshield {
    if (system("which unshield > /dev/null 2>&1")) {
	die "This firmware requires the unshield command - see http://sourceforge.net/projects/synce/\n";
    }
}

sub wgetfile {
    my ($sourcefile, $url) = @_;

    if (! -f $sourcefile) {
	system("wget -O \"$sourcefile\" \"$url\"") and die "wget failed - unable to download firmware";
    }
}

sub unzip {
    my ($sourcefile, $todir) = @_;

    $status = system("unzip -q -o -d \"$todir\" \"$sourcefile\" 2>/dev/null" );
    if ((($status >> 8) > 2) || (($status & 0xff) != 0)) {
	die ("unzip failed - unable to extract firmware");
    }
}

sub unshield {
    my ($sourcefile, $todir) = @_;

    system("unshield x -d \"$todir\" \"$sourcefile\" > /dev/null" ) and die ("unshield failed - unable to extract firmware");
}

sub verify {
    my ($filename, $hash) = @_;
    my ($testhash);

    open(CMD, "md5sum \"$filename\"|");
    $testhash = <CMD>;
    $testhash =~ /([a-zA-Z0-9]*)/;
    $testhash = $1;
    close CMD;
    die "Hash of extracted file does not match!\n" if ($testhash ne $hash);
}

sub copy {
    my ($from, $to) = @_;

    system("cp -f \"$from\" \"$to\"") and die ("cp failed");
}

sub extract {
    my ($infile, $offset, $length, $outfile) = @_;
    my ($chunklength, $buf, $rcount);

    open INFILE, "<$infile";
    open OUTFILE, ">$outfile";
    sysseek(INFILE, $offset, SEEK_SET);
    while($length > 0) {
	# Calc chunk size
	$chunklength = 2048;
	$chunklength = $length if ($chunklength > $length);

	$rcount = sysread(INFILE, $buf, $chunklength);
	die "Ran out of data\n" if ($rcount != $chunklength);
	syswrite(OUTFILE, $buf);
	$length -= $rcount;
    }
    close INFILE;
    close OUTFILE;
}

sub appendfile {
    my ($FH, $infile) = @_;
    my ($buf);

    open INFILE, "<$infile";
    while(1) {
	$rcount = sysread(INFILE, $buf, 2048);
	last if ($rcount == 0);
	print $FH $buf;
    }
    close(INFILE);
}

sub delzero{
	my ($infile,$outfile) =@_;

	open INFILE,"<$infile";
	open OUTFILE,">$outfile";
	while (1){
		$rcount=sysread(INFILE,$buf,22);
		$len=ord(substr($buf,0,1));
		print OUTFILE substr($buf,0,1);
		print OUTFILE substr($buf,2,$len+3);
	last if ($rcount<1);
	printf OUTFILE "%c",0;
#print $len." ".length($buf)."\n";

	}
	close(INFILE);
	close(OUTFILE);
}

sub syntax() {
    print STDERR "syntax: get_dvb_firmware <component>\n";
    print STDERR "Supported components:\n";
    @components = sort @components;
    for($i=0; $i < scalar(@components); $i++) {
	print STDERR "\t" . $components[$i] . "\n";
    }
    exit(1);
}

```

---

### Post by jonathan-l-harrison on 2014-06-23
Tried that...
First time using the code from the eMail notification, which threw up errors.  Just done again from the Forum reply 
```
sudo perl /home/mediaserver/WINTv\ 4400\ Drive
```

I DID A RESTART ANYWAY AS SUGGESTED AND GOT THE FOLLOWING WHEN I DID ```
**dmesg**
```

```
[    1.456706] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H66N  CB00 PQ: 0 ANSI: 5
[    1.460634] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.460635] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.460735] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.460788] sr 5:0:0:0: Attached scsi generic sg0 type 5
[    1.513827] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.513829] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.513984] hub 2-1:1.0: USB hub found
[    1.514078] hub 2-1:1.0: 8 ports detected
[    1.585642] usb 1-1.6: new full-speed USB device number 3 using ehci-pci
[    1.678745] usb 1-1.6: New USB device found, idVendor=0b05, idProduct=179c
[    1.678747] usb 1-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.689684] tsc: Refined TSC clocksource calibration: 3699.953 MHz
[    1.785815] usb 2-1.2: new full-speed USB device number 3 using ehci-pci
[    1.883542] usb 2-1.2: New USB device found, idVendor=045e, idProduct=0745
[    1.883544] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.883545] usb 2-1.2: Product: Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0
[    1.883546] usb 2-1.2: Manufacturer: Microsoft
[    1.885854] hidraw: raw HID events driver (C) Jiri Kosina
[    1.898939] usbcore: registered new interface driver usbhid
[    1.898940] usbhid: USB HID core driver
[    1.900020] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    1.900096] hid-generic 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:1d.0-1.2/input0
[    1.900288] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input6
[    1.900390] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:1d.0-1.2/input1
[    1.910260] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.2/input/input7
[    1.910367] hid-generic 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v8.0] on usb-0000:00:1d.0-1.2/input2
[    1.949919] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.990723] ata8.00: ATA-9: ST1000DX001-1CM162, CC43, max UDMA/133
[    1.990725] ata8.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.024084] ata8.00: configured for UDMA/133
[    2.024188] scsi 7:0:0:0: Direct-Access     ATA      ST1000DX001-1CM1 CC43 PQ: 0 ANSI: 5
[    2.024289] sd 7:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.024291] sd 7:0:0:0: [sda] 4096-byte physical blocks
[    2.024297] sd 7:0:0:0: Attached scsi generic sg1 type 0
[    2.024364] sd 7:0:0:0: [sda] Write Protect is off
[    2.024366] sd 7:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.024390] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.025128]  sda: sda1 sda2 sda3
[    2.025342] sd 7:0:0:0: [sda] Attached SCSI disk
[    2.342264] ata10: SATA link down (SStatus 0 SControl 300)
[    2.454355] nouveau  [  PTHERM][0000:04:00.0] FAN control: PWM
[    2.454367] nouveau  [  PTHERM][0000:04:00.0] fan management: automatic
[    2.454370] nouveau  [  PTHERM][0000:04:00.0] internal sensor: yes
[    2.454394] nouveau  [     CLK][0000:04:00.0] 03: core 50 MHz memory 135 MHz 
[    2.454395] nouveau  [     CLK][0000:04:00.0] 07: core 405 MHz memory 324 MHz 
[    2.454396] nouveau  [     CLK][0000:04:00.0] 0f: core 700 MHz memory 800 MHz 
[    2.454534] nouveau  [     CLK][0000:04:00.0] --: core 405 MHz memory 324 MHz 
[    2.458919] [TTM] Zone  kernel: Available graphics memory: 16443156 kiB
[    2.458920] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    2.458920] [TTM] Initializing pool allocator
[    2.458922] [TTM] Initializing DMA pool allocator
[    2.458927] nouveau  [     DRM] VRAM: 512 MiB
[    2.458928] nouveau  [     DRM] GART: 1048576 MiB
[    2.458930] nouveau  [     DRM] TMDS table version 2.0
[    2.458931] nouveau  [     DRM] DCB version 4.0
[    2.458933] nouveau  [     DRM] DCB outp 00: 01000302 00020030
[    2.458934] nouveau  [     DRM] DCB outp 01: 02000300 00000000
[    2.458934] nouveau  [     DRM] DCB outp 02: 08011392 00020020
[    2.458935] nouveau  [     DRM] DCB outp 03: 04022310 00000000
[    2.458936] nouveau  [     DRM] DCB conn 00: 00001030
[    2.458937] nouveau  [     DRM] DCB conn 01: 00002161
[    2.458938] nouveau  [     DRM] DCB conn 02: 00000200
[    2.459540] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.459541] [drm] No driver support for vblank timestamp query.
[    2.466610] nouveau  [     DRM] MM: using COPY0 for buffer copies
[    2.589199] nouveau  [     DRM] allocated 1920x1080 fb: 0x60000, bo ffff8807f3a55400
[    2.589230] fbcon: nouveaufb (fb0) is primary device
[    2.656755] Console: switching to colour frame buffer device 240x67
[    2.658721] nouveau 0000:04:00.0: fb0: nouveaufb frame buffer device
[    2.658722] nouveau 0000:04:00.0: registered panic notifier
[    2.658724] [drm] Initialized nouveau 1.1.1 20120801 for 0000:04:00.0 on minor 0
[    2.690618] Switched to clocksource tsc
[    2.870605] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.096135] random: init urandom read with 55 bits of entropy available
[    5.188525] Adding 29296636k swap on /dev/sda2.  Priority:-1 extents:1 across:29296636k FS
[    5.198780] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.219591] systemd-udevd[376]: starting version 204
[    5.246055] lp: driver loaded but no devices found
[    5.248980] ppdev: user-space parallel port driver
[    5.262803] random: nonblocking pool is initialized
[    5.314968] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    5.321721] mei_me 0000:00:16.0: irq 101 for MSI/MSI-X
[    5.327072] Bluetooth: Core ver 2.17
[    5.327083] NET: Registered protocol family 31
[    5.327084] Bluetooth: HCI device and connection manager initialized
[    5.327090] Bluetooth: HCI socket layer initialized
[    5.327092] Bluetooth: L2CAP socket layer initialized
[    5.327095] Bluetooth: SCO socket layer initialized
[    5.328258] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20131115/utaddress-251)
[    5.328263] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.328264] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.SBRG.GPBX 1 (20131115/utaddress-251)
[    5.328267] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.328268] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    5.329101] usbcore: registered new interface driver btusb
[    5.333341] EDAC MC: Ver: 3.0.0
[    5.334908] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[    5.334915] EDAC sbridge: Seeking for: dev 0e.0 PCI ID 8086:0ea0
[    5.334917] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[    5.334921] EDAC sbridge: Seeking for: dev 0f.0 PCI ID 8086:0ea8
[    5.334923] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[    5.334926] EDAC sbridge: Seeking for: dev 0f.1 PCI ID 8086:0e71
[    5.334928] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[    5.334931] EDAC sbridge: Seeking for: dev 0f.2 PCI ID 8086:0eaa
[    5.334933] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[    5.334936] EDAC sbridge: Seeking for: dev 0f.3 PCI ID 8086:0eab
[    5.334937] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[    5.334941] EDAC sbridge: Seeking for: dev 0f.4 PCI ID 8086:0eac
[    5.334942] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[    5.334946] EDAC sbridge: Seeking for: dev 0f.5 PCI ID 8086:0ead
[    5.334947] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[    5.334951] EDAC sbridge: Seeking for: dev 16.0 PCI ID 8086:0ec8
[    5.334952] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[    5.334956] EDAC sbridge: Seeking for: dev 16.1 PCI ID 8086:0ec9
[    5.334957] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[    5.334960] EDAC sbridge: Seeking for: dev 16.2 PCI ID 8086:0eca
[    5.334962] EDAC sbridge: Seeking for: dev 1c.0 PCI ID 8086:0e60
[    5.334965] EDAC sbridge: Seeking for: dev 1d.2 PCI ID 8086:0e6a
[    5.334968] EDAC sbridge: Seeking for: dev 1d.3 PCI ID 8086:0e6b
[    5.334970] EDAC sbridge: Seeking for: dev 11.0 PCI ID 8086:0eb8
[    5.334973] EDAC sbridge: Seeking for: dev 11.4 PCI ID 8086:0ebc
[    5.334977] EDAC sbridge: ECC is disabled. Aborting
[    5.334978] EDAC sbridge: Couldn't find mci handler
[    5.355139] snd_hda_intel 0000:00:1b.0: irq 102 for MSI/MSI-X
[    5.371770] SKU: Nid=0x1d sku_cfg=0x4007e629
[    5.371772] SKU: port_connectivity=0x1
[    5.371773] SKU: enable_pcbeep=0x0
[    5.371773] SKU: check_sum=0x00000007
[    5.371774] SKU: customization=0x000000e6
[    5.371774] SKU: external_amp=0x5
[    5.371775] SKU: platform_type=0x0
[    5.371775] SKU: swap=0x0
[    5.371776] SKU: override=0x1
[    5.372192] autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    5.372192]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.372193]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    5.372193]    mono: mono_out=0x0
[    5.372194]    dig-out=0x11/0x1e
[    5.372194]    inputs:
[    5.372195]      Front Mic=0x19
[    5.372196]      Rear Mic=0x18
[    5.372197]      Line=0x1a
[    5.372197] realtek: No valid SSID, checking pincfg 0x4007e629 for NID 0x1d
[    5.372198] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0899
[    5.381751] media: module verification failed: signature and/or  required key missing - tainting kernel
[    5.382019] media: Linux media interface: v0.10
[    5.383067] videodev: module has bad taint, not creating trace events
[    5.383092] Linux video capture interface: v2.00
[    5.383093] WARNING: You are using an experimental version of the media stack.
[    5.383093]     As the driver is backported to an older kernel, it doesn't offer
[    5.383093]     enough quality for its usage in production.
[    5.383093]     Use it with care.
[    5.383093] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[    5.383093]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[    5.383093]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[    5.383093]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[    5.383510] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    5.383562] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    5.383602] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    5.383646] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    5.383686] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.383730] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.383761] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.383926] hda_intel: Disabling MSI
[    5.383933] hda-intel 0000:04:00.1: Handle VGA-switcheroo audio client
[    5.383959] hda-intel 0000:04:00.1: Disabling 64bit DMA
[    5.386454] WARNING: You are using an experimental version of the media stack.
[    5.386454]     As the driver is backported to an older kernel, it doesn't offer
[    5.386454]     enough quality for its usage in production.
[    5.386454]     Use it with care.
[    5.386454] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[    5.386454]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[    5.386454]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[    5.386454]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[    5.388748] WARNING: You are using an experimental version of the media stack.
[    5.388748]     As the driver is backported to an older kernel, it doesn't offer
[    5.388748]     enough quality for its usage in production.
[    5.388748]     Use it with care.
[    5.388748] Latest git patches (needed if you report a bug to linux-media@vger.kernel.org):
[    5.388748]     5ea878796f0a1d9649fe43a6a09df53d3915c0ef [media] V4L2: soc_camera: Add run-time dependencies to sh_mobile drivers
[    5.388748]     52e1473a58b6ea5d9b4ea3d4a0af8b59166aab42 [media] media: mx2_camera: Change Kconfig dependency
[    5.388748]     58be734f53089525224abc2e8ef75d1e9574a423 [media] media: mx1_camera: Remove driver
[    5.389144] hda-intel 0000:04:00.1: Enable delay in RIRB handling
[    5.398074] type=1400 audit(1403521421.817:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=589 comm="apparmor_parser"
[    5.398080] type=1400 audit(1403521421.817:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=589 comm="apparmor_parser"
[    5.398083] type=1400 audit(1403521421.817:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=589 comm="apparmor_parser"
[    5.398356] type=1400 audit(1403521421.817:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=589 comm="apparmor_parser"
[    5.398359] type=1400 audit(1403521421.817:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=589 comm="apparmor_parser"
[    5.398481] type=1400 audit(1403521421.817:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=589 comm="apparmor_parser"
[    5.399292] cx23885 driver version 0.0.3 loaded
[    5.399485] CORE cx23885[0]: subsystem: 0070:c108, board: Hauppauge WinTV-HVR4400 [card=38,autodetected]
[    5.400325] type=1400 audit(1403521421.817:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=599 comm="apparmor_parser"
[    5.406291] asus_wmi: ASUS WMI generic driver loaded
[    5.407653] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    5.407754] asus_wmi: Initialization: 0x0
[    5.407771] asus_wmi: BIOS WMI version: 0.9
[    5.407801] asus_wmi: SFUN value: 0x0
[    5.408026] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input15
[    5.408513] asus_wmi: Disabling ACPI video driver
[    5.504742] FS-Cache: Loaded
[    5.512221] RPC: Registered named UNIX socket transport module.
[    5.512223] RPC: Registered udp transport module.
[    5.512223] RPC: Registered tcp transport module.
[    5.512224] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    5.520405] FS-Cache: Netfs 'nfs' registered for caching
[    5.531188] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    5.549387] init: idmapd main process (699) terminated with status 1
[    5.549394] init: idmapd main process ended, respawning
[    5.557560] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.557562] Bluetooth: BNEP filters: protocol multicast
[    5.557568] Bluetooth: BNEP socket layer initialized
[    5.558557] Bluetooth: RFCOMM TTY layer initialized
[    5.558562] Bluetooth: RFCOMM socket layer initialized
[    5.558566] Bluetooth: RFCOMM ver 1.11
[    5.574682] type=1400 audit(1403521421.993:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=767 comm="apparmor_parser"
[    5.574687] type=1400 audit(1403521421.993:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=767 comm="apparmor_parser"
[    5.617854] init: failsafe main process (745) killed by TERM signal
[    5.631802] init: cups main process (788) killed by HUP signal
[    5.631810] init: cups main process ended, respawning
[    5.642820] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[    5.701724] audit_printk_skb: 3 callbacks suppressed
[    5.701726] type=1400 audit(1403521422.121:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=928 comm="apparmor_parser"
[    5.701730] type=1400 audit(1403521422.121:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=928 comm="apparmor_parser"
[    5.701732] type=1400 audit(1403521422.121:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=928 comm="apparmor_parser"
[    5.701950] type=1400 audit(1403521422.121:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=928 comm="apparmor_parser"
[    5.701952] type=1400 audit(1403521422.121:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=928 comm="apparmor_parser"
[    5.702067] type=1400 audit(1403521422.121:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=928 comm="apparmor_parser"
[    5.702228] type=1400 audit(1403521422.121:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=927 comm="apparmor_parser"
[    5.702233] type=1400 audit(1403521422.121:19): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=927 comm="apparmor_parser"
[    5.702397] type=1400 audit(1403521422.121:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=927 comm="apparmor_parser"
[    5.706348] type=1400 audit(1403521422.125:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=931 comm="apparmor_parser"
[    5.725550] tveeprom 12-0050: Hauppauge model 121019, rev B2F5, serial# 8647267
[    5.725553] tveeprom 12-0050: MAC address is 00:0d:fe:83:f2:63
[    5.725554] tveeprom 12-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[    5.725555] tveeprom 12-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[    5.725555] tveeprom 12-0050: audio processor is CX23888 (idx 40)
[    5.725556] tveeprom 12-0050: decoder processor is CX23888 (idx 34)
[    5.725557] tveeprom 12-0050: has radio, has IR receiver, has no IR transmitter
[    5.725558] cx23885[0]: warning: unknown hauppauge model #121019
[    5.725558] cx23885[0]: hauppauge eeprom: model=121019
[    5.725560] cx23885_dvb_register() allocating 1 frontend(s)
[    5.725563] cx23885[0]: cx23885 based dvb card
[    5.734771] i2c i2c-12: a8293: Allegro A8293 SEC attached
[    5.734773] DVB: registering new adapter (cx23885[0])
[    5.734776] cx23885 0000:06:00.0: DVB: registering adapter 0 frontend 0 (NXP TDA10071)...
[    5.734937] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    5.734941] cx23885[0]/0: found at 0000:06:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfb200000
[    5.754271] init: samba-ad-dc main process (878) terminated with status 1
[    5.915660] init: nvidia-prime main process (1052) terminated with status 127
[    5.916650] zram: module is from the staging directory, the quality is unknown, you have been warned.
[    5.916730] e1000e 0000:00:19.0: irq 98 for MSI/MSI-X
[    5.919033] zram: Created 8 device(s) ...
[    5.924103] Adding 2055392k swap on /dev/zram0.  Priority:5 extents:1 across:2055392k SSFS
[    5.927173] Adding 2055392k swap on /dev/zram1.  Priority:5 extents:1 across:2055392k SSFS
[    5.929644] Adding 2055392k swap on /dev/zram2.  Priority:5 extents:1 across:2055392k SSFS
[    5.932292] Adding 2055392k swap on /dev/zram3.  Priority:5 extents:1 across:2055392k SSFS
[    5.935066] Adding 2055392k swap on /dev/zram4.  Priority:5 extents:1 across:2055392k SSFS
[    5.937989] Adding 2055392k swap on /dev/zram5.  Priority:5 extents:1 across:2055392k SSFS
[    5.941208] Adding 2055392k swap on /dev/zram6.  Priority:5 extents:1 across:2055392k SSFS
[    5.944353] Adding 2055392k swap on /dev/zram7.  Priority:5 extents:1 across:2055392k SSFS
[    6.017460] e1000e 0000:00:19.0: irq 98 for MSI/MSI-X
[    6.017559] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.017775] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.025405] init: isc-dhcp-server main process (1114) terminated with status 1
[    6.025415] init: isc-dhcp-server main process ended, respawning
[    6.027864] init: tftpd-hpa main process (1126) terminated with status 66
[    6.027874] init: tftpd-hpa main process ended, respawning
[    6.092985] init: isc-dhcp-server main process (1401) terminated with status 1
[    6.092993] init: isc-dhcp-server main process ended, respawning
[    6.111056] init: mythbuntu-bare-console main process (1331) terminated with status 1
[    6.111065] init: mythbuntu-bare-console main process ended, respawning
[    6.117594] init: mythbuntu-bare-console-processor main process (1336) terminated with status 1
[    6.117603] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.123048] init: isc-dhcp-server main process (1481) terminated with status 1
[    6.123059] init: isc-dhcp-server main process ended, respawning
[    6.153944] init: isc-dhcp-server main process (1499) terminated with status 1
[    6.153956] init: isc-dhcp-server main process ended, respawning
[    6.171862] init: mythbuntu-bare-console main process (1487) terminated with status 1
[    6.171870] init: mythbuntu-bare-console main process ended, respawning
[    6.186701] init: isc-dhcp-server main process (1513) terminated with status 1
[    6.186713] init: isc-dhcp-server main process ended, respawning
[    6.203422] init: mythbuntu-bare-console-processor main process (1489) terminated with status 1
[    6.203434] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.219077] init: isc-dhcp-server main process (1527) terminated with status 1
[    6.219089] init: isc-dhcp-server main process ended, respawning
[    6.237948] init: mythbuntu-bare-console main process (1523) terminated with status 1
[    6.237961] init: mythbuntu-bare-console main process ended, respawning
[    6.243759] init: isc-dhcp-server main process (1542) terminated with status 1
[    6.243769] init: isc-dhcp-server main process ended, respawning
[    6.267160] init: isc-dhcp-server main process (1552) terminated with status 1
[    6.267171] init: isc-dhcp-server main process ended, respawning
[    6.288662] init: mythbuntu-bare-console-processor main process (1533) terminated with status 1
[    6.288672] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.296671] init: isc-dhcp-server main process (1560) terminated with status 1
[    6.296682] init: isc-dhcp-server main process ended, respawning
[    6.308068] init: mythbuntu-bare-console main process (1548) terminated with status 1
[    6.308078] init: mythbuntu-bare-console main process ended, respawning
[    6.320638] init: isc-dhcp-server main process (1570) terminated with status 1
[    6.320649] init: isc-dhcp-server main process ended, respawning
[    6.346482] init: isc-dhcp-server main process (1582) terminated with status 1
[    6.346495] init: isc-dhcp-server respawning too fast, stopped
[    6.372646] init: mythbuntu-bare-console-processor main process (1566) terminated with status 1
[    6.372655] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.372885] init: mythbuntu-bare-console main process (1576) terminated with status 1
[    6.372891] init: mythbuntu-bare-console main process ended, respawning
[    6.443230] init: mythbuntu-bare-console main process (1598) terminated with status 1
[    6.443243] init: mythbuntu-bare-console main process ended, respawning
[    6.452734] init: mythbuntu-bare-console-processor main process (1595) terminated with status 1
[    6.452747] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.491299] init: plymouth-upstart-bridge main process ended, respawning
[    6.495922] init: plymouth-upstart-bridge main process (1638) terminated with status 1
[    6.495933] init: plymouth-upstart-bridge main process ended, respawning
[    6.516227] init: mythbuntu-bare-console main process (1631) terminated with status 1
[    6.516238] init: mythbuntu-bare-console main process ended, respawning
[    6.543008] init: mythbuntu-bare-console-processor main process (1633) terminated with status 1
[    6.543018] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.577514] init: mythbuntu-bare-console main process (1650) terminated with status 1
[    6.577525] init: mythbuntu-bare-console main process ended, respawning
[    6.615174] init: mythbuntu-bare-console-processor main process (1664) terminated with status 1
[    6.615183] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.647746] init: mythbuntu-bare-console main process (1712) terminated with status 1
[    6.647760] init: mythbuntu-bare-console main process ended, respawning
[    6.687710] init: mythbuntu-bare-console-processor main process (1726) terminated with status 1
[    6.687720] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.730949] init: mythbuntu-bare-console main process (1741) terminated with status 1
[    6.730962] init: mythbuntu-bare-console main process ended, respawning
[    6.760045] init: mythbuntu-bare-console-processor main process (1747) terminated with status 1
[    6.760054] init: mythbuntu-bare-console-processor main process ended, respawning
[    6.789048] init: mythbuntu-bare-console main process (1762) terminated with status 1
[    6.789061] init: mythbuntu-bare-console respawning too fast, stopped
[    6.792817] init: mythbuntu-bare-console-processor main process (1777) killed by TERM signal
[    6.962320] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input19
[    6.962369] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input18
[    6.962405] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input17
[    6.962437] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.2/0000:04:00.1/sound/card1/input16
[    7.704565] init: plymouth-stop pre-start process (1893) terminated with status 1
[    9.605442] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    9.605473] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.181582] init: mythtv-backend main process (2545) terminated with status 135
[   14.181591] init: mythtv-backend main process ended, respawning
[   35.649697] audit_printk_skb: 144 callbacks suppressed
[   35.649699] type=1400 audit(1403521452.048:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3217 comm="apparmor_parser"
[   35.649703] type=1400 audit(1403521452.048:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3217 comm="apparmor_parser"
[   35.649923] type=1400 audit(1403521452.048:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3217 comm="apparmor_parser"
[   92.533061] traps: notify-osd[3028] trap int3 ip:7f4a45412c13 sp:7fff1a4a76f0 error:0

```

---

### Post by xc3RnbFO8P on 2014-06-23
There is no change.
>  Hauppauge UK Forums (moderator wrote this in December 2010; no news by Feb 2012):
It is dead, I cant find anything to make it work, only dead links.

---

### Post by jonathan-l-harrison on 2014-06-23
when setting up Me Tv this is what I get
[ATTACH=CONFIG]254185[/ATTACH]

I found these, including a site with Linux drivers and Firmware (can't seem to find) but it is all a bit too advanced for me to action.
[URL="http://www.linuxtv.org/wiki/index.php/Hauppauge"]http://linuxtv.org/repo/
http://www.linuxtv.org/wiki/index.php/Hauppauge[/URL]
[http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware)
[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device)
[http://www.linuxtv.org/wiki/index.php/Dvbscan#Creating_a_channels.conf_file](http://www.linuxtv.org/wiki/index.php/Dvbscan#Creating_a_channels.conf_file)
[http://wiki.linuxmce.org/index.php/Capture_Cards](http://wiki.linuxmce.org/index.php/Capture_Cards)
[http://www.linuxtv.org/wiki/index.php?title=Hauppauge_WinTV-HVR-4400&action=history](http://www.linuxtv.org/wiki/index.php?title=Hauppauge_WinTV-HVR-4400&action=history)

---

### Post by xc3RnbFO8P on 2014-06-23
You can see in screenshot that autoscanning is grayed out, because there is no (digital) dvb-t or atsc device.
There is only digital brodcast in England and EU.

---

### Post by jonathan-l-harrison on 2014-06-23
That can't be it...

So what alternatives have I...  This card is supposed to be terrestrial Tv, Freeview and Satellite (which I think works.  Not plugged in the dish, but it scans).

---


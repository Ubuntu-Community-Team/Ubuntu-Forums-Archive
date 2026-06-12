---
title: "Sound Probs"
date: 2012-06-03
forum: Multimedia Software
---

### Post by westag on 2012-06-03
The Problem:

if I play Second Life, the game, it takes over my sound on the rest of my computer...so for instance, before I play, all sounds work: system sounds, videos, music, youtube videos...but once I login to Second Life, I can only hear sound on Second Life and no where else. 

When Second Life is running if I try:

**aplay /usr/share/sounds/alsa/Front_Center.wav**

```
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:654: audio open error: Device or resource busy

```

**lsof | grep pcm **

```

pulseaudi  2417       abram  mem       CHR              116,7                 4692 /dev/snd/pcmC0D0p
pulseaudi  2417       abram   41u      CHR              116,7       0t0       4692 /dev/snd/pcmC0D0p

```




**lspci -vnn**
```

00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Flags: fast devsel, IRQ 11
	Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot-), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>

00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fb800000-fb8fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport

00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fb600000-fb6fffff
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport

00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fb500000-fb5fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport

00:05.0 PCI bridge [0604]: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 [8086:340c] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport

00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport

00:09.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 [8086:3410] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport

00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [50] Vendor Specific Information: Len=ff <?>

00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:11.0 PIC [0800]: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [50] #00 [0000]

00:11.1 PIC [0800]: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:13.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13) (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [6c] Power Management version 3

00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:15.0 PIC [0800]: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13) (prog-if 20 [IO(X)-APIC])
	Flags: fast devsel

00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at fe00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fd00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c] (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5006]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fbffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:a102]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fbff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0100000-f02fffff
	Prefetchable memory behind bridge: 00000000f0300000-00000000f04fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000f0500000-00000000f06fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbd00000-fbdfffff
	Prefetchable memory behind bridge: 00000000f0700000-00000000f08fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbc00000-fbcfffff
	Prefetchable memory behind bridge: 00000000fbb00000-00000000fbbfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fba00000-fbafffff
	Prefetchable memory behind bridge: 00000000fb900000-00000000fb9fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at fc00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fb00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fa00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a] (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5006]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fbffd000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
	Memory behind bridge: fb700000-fb7fffff
	Capabilities: [50] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5000]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822]
	Subsystem: Giga-byte Technology Device [1458:b000]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 35
	I/O ports at f900 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f700 [size=8]
	I/O ports at f600 [size=4]
	I/O ports at f500 [size=32]
	Memory at fbffc000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Flags: medium devsel, IRQ 18
	Memory at fbffb000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel driver in use: i801_smbus

01:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9128] (rev 11) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology Device [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 38
	I/O ports at af00 [size=8]
	I/O ports at ae00 [size=4]
	I/O ports at ad00 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at ab00 [size=16]
	Memory at fb8ff000 (32-bit, non-prefetchable) [size=2K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: ahci

02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03) (prog-if 30)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fb6fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [50] Power Management version 3
	Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [90] MSI-X: Enable- Count=8 Masked-
	Capabilities: [a0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
	Capabilities: [150] #18
	Kernel driver in use: xhci_hcd

03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV790 [Radeon HD 4800 Series] [1002:9460] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Device [174b:e115]
	Flags: bus master, fast devsel, latency 0, IRQ 39
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb5e0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at be00 [size=256]
	[virtual] Expansion ROM at fb500000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: fglrx_pci

03:00.1 Audio device [0403]: ATI Technologies Inc HD48x0 audio [1002:aa30]
	Subsystem: PC Partner Limited Sapphire HD 4850 512MB GDDR3 PCI-E Dual Slot Fansink [174b:aa30]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fb5fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: HDA Intel

08:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbefe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint, MSI 01
	Kernel driver in use: ahci

08:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at 9f00 [size=8]
	I/O ports at 9e00 [size=4]
	I/O ports at 9d00 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9b00 [size=16]
	Capabilities: [68] Power Management version 2
	Kernel driver in use: pata_jmicron

09:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint, MSI 01
	Kernel driver in use: ahci

09:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at ef00 [size=8]
	I/O ports at ee00 [size=4]
	I/O ports at ed00 [size=8]
	I/O ports at ec00 [size=4]
	I/O ports at eb00 [size=16]
	Capabilities: [68] Power Management version 2
	Kernel driver in use: pata_jmicron

0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Flags: bus master, fast devsel, latency 0, IRQ 36
	I/O ports at de00 [size=256]
	Memory at fbbff000 (64-bit, prefetchable) [size=4K]
	Memory at fbbf8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fbb00000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 04-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169

0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Flags: bus master, fast devsel, latency 0, IRQ 37
	I/O ports at ce00 [size=256]
	Memory at fb9ff000 (64-bit, prefetchable) [size=4K]
	Memory at fb9f8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fb900000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 04-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169

0c:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:1000]
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fb7ff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fb7f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: firewire_ohci

00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
	Subsystem: Giga-byte Technology Device [1458:5000]
	Flags: fast devsel, IRQ 11
	Capabilities: [60] MSI: Enable- Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot-), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>

00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fb800000-fb8fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport

00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fb600000-fb6fffff
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport

00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fb500000-fb5fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport

00:05.0 PCI bridge [0604]: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 [8086:340c] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport

00:07.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 [8086:340e] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Capabilities: [160] Vendor Specific Information: ID=0002 Rev=0 Len=00c <?>
	Kernel driver in use: pcieport

00:09.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 9 [8086:3410] (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: [40] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [60] MSI: Enable+ Count=1/2 Maskable+ 64bit-
	Capabilities: [90] Express Root Port (Slot+), MSI 00
	Capabilities: [e0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [150] Access Control Services
	Kernel driver in use: pcieport

00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [50] Vendor Specific Information: Len=ff <?>

00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:11.0 PIC [0800]: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [50] #00 [0000]

00:11.1 PIC [0800]: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:13.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13) (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [6c] Power Management version 3

00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00

00:15.0 PIC [0800]: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13) (prog-if 20 [IO(X)-APIC])
	Flags: fast devsel

00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at fe00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fd00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c] (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5006]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fbffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:a102]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fbff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0100000-f02fffff
	Prefetchable memory behind bridge: 00000000f0300000-00000000f04fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000f0500000-00000000f06fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology Device [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbd00000-fbdfffff
	Prefetchable memory behind bridge: 00000000f0700000-00000000f08fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbc00000-fbcfffff
	Prefetchable memory behind bridge: 00000000fbb00000-00000000fbbfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a] (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fba00000-fbafffff
	Prefetchable memory behind bridge: 00000000fb900000-00000000fb9fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport

00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at fc00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fb00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36] (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5004]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fa00 [size=32]
	Capabilities: [50] PCI Advanced Features
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a] (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5006]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fbffd000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
	Memory behind bridge: fb700000-fb7fffff
	Capabilities: [50] Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5000]

00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822]
	Subsystem: Giga-byte Technology Device [1458:b000]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 35
	I/O ports at f900 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f700 [size=8]
	I/O ports at f600 [size=4]
	I/O ports at f500 [size=32]
	Memory at fbffc000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/16 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:5001]
	Flags: medium devsel, IRQ 18
	Memory at fbffb000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel driver in use: i801_smbus

01:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9128] (rev 11) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology Device [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 38
	I/O ports at af00 [size=8]
	I/O ports at ae00 [size=4]
	I/O ports at ad00 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at ab00 [size=16]
	Memory at fb8ff000 (32-bit, non-prefetchable) [size=2K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: ahci

02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03) (prog-if 30)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fb6fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [50] Power Management version 3
	Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
	Capabilities: [90] MSI-X: Enable- Count=8 Masked-
	Capabilities: [a0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
	Capabilities: [150] #18
	Kernel driver in use: xhci_hcd

03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV790 [Radeon HD 4800 Series] [1002:9460] (prog-if 00 [VGA controller])
	Subsystem: PC Partner Limited Device [174b:e115]
	Flags: bus master, fast devsel, latency 0, IRQ 39
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb5e0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at be00 [size=256]
	[virtual] Expansion ROM at fb500000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: fglrx_pci

03:00.1 Audio device [0403]: ATI Technologies Inc HD48x0 audio [1002:aa30]
	Subsystem: PC Partner Limited Sapphire HD 4850 512MB GDDR3 PCI-E Dual Slot Fansink [174b:aa30]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fb5fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: HDA Intel

08:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbefe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint, MSI 01
	Kernel driver in use: ahci

08:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at 9f00 [size=8]
	I/O ports at 9e00 [size=4]
	I/O ports at 9d00 [size=8]
	I/O ports at 9c00 [size=4]
	I/O ports at 9b00 [size=16]
	Capabilities: [68] Power Management version 2
	Kernel driver in use: pata_jmicron

09:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [68] Power Management version 2
	Capabilities: [50] Express Legacy Endpoint, MSI 01
	Kernel driver in use: ahci

09:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:b000]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at ef00 [size=8]
	I/O ports at ee00 [size=4]
	I/O ports at ed00 [size=8]
	I/O ports at ec00 [size=4]
	I/O ports at eb00 [size=16]
	Capabilities: [68] Power Management version 2
	Kernel driver in use: pata_jmicron

0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Flags: bus master, fast devsel, latency 0, IRQ 36
	I/O ports at de00 [size=256]
	Memory at fbbff000 (64-bit, prefetchable) [size=4K]
	Memory at fbbf8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fbb00000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 04-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169

0b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Flags: bus master, fast devsel, latency 0, IRQ 37
	I/O ports at ce00 [size=256]
	Memory at fb9ff000 (64-bit, prefetchable) [size=4K]
	Memory at fb9f8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fb900000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 04-00-00-00-68-4c-e0-00
	Kernel driver in use: r8169

0c:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:1000]
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fb7ff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fb7f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: firewire_ohci

```
**lsmod**

```

Module                  Size  Used by
sco                     7225  2 
parport_pc             18855  0 
ppdev                   5030  0 
bridge                 39646  0 
stp                     1440  1 bridge
lp                      7462  0 
bnep                    9427  2 
parport                27954  3 parport_pc,ppdev,lp
rfcomm                 29629  0 
l2cap                  24752  6 bnep,rfcomm
bluetooth              41827  6 sco,bnep,rfcomm,l2cap
rfkill                 13044  2 bluetooth
acpi_cpufreq            5571  0 
cpufreq_userspace       1992  0 
cpufreq_conservative     5162  0 
cpufreq_powersave        902  0 
cpufreq_stats           2740  0 
binfmt_misc             6431  1 
fuse                   50924  1 
snd_hda_codec_atihdmi     2251  1 
snd_hda_codec_realtek   235714  1 
snd_hda_intel          20035  7 
snd_hda_codec          54292  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5380  1 snd_hda_codec
snd_pcm_oss            32591  0 
snd_mixer_oss          12606  2 snd_pcm_oss
snd_pcm                60487  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi            4400  0 
snd_rawmidi            15515  1 snd_seq_midi
snd_seq_midi_event      4628  1 snd_seq_midi
snd_seq                42881  2 snd_seq_midi,snd_seq_midi_event
snd_timer              15598  2 snd_pcm,snd_seq
snd_seq_device          4493  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    46526  22 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               4598  2 snd
snd_page_alloc          6249  2 snd_hda_intel,snd_pcm
loop                   11799  0 
firewire_sbp2          11514  0 
i2c_i801                7830  0 
pcspkr                  1699  0 
i2c_core               15819  1 i2c_i801
wmi                     4323  0 
joydev                  8459  0 
serio_raw               3752  0 
evdev                   7352  17 
fglrx                2452362  992 
button                  4650  0 
processor              29935  1 acpi_cpufreq
ext4                  288382  3 
mbcache                 5050  1 ext4
jbd2                   67111  1 ext4
crc16                   1319  2 l2cap,ext4
sr_mod                 12602  0 
hid_logitech            6326  0 
sg                     24069  0 
firewire_ohci          19676  0 
cdrom                  29351  1 sr_mod
ff_memless              3692  1 hid_logitech
sd_mod                 29937  5 
crc_t10dif              1276  1 sd_mod
firewire_core          36848  2 firewire_sbp2,firewire_ohci
usbhid                 33292  1 hid_logitech
hid                    63257  2 hid_logitech,usbhid
usb_storage            40217  0 
uhci_hcd               18521  0 
xhci                   34041  0 
crc_itu_t               1307  1 firewire_core
r8169                  36840  0 
ehci_hcd               32097  0 
mii                     3210  1 r8169
ata_generic             3239  0 
ahci                   32870  3 
pata_jmicron            2280  0 
libata                133776  3 ata_generic,ahci,pata_jmicron
usbcore               123122  6 usbhid,usb_storage,uhci_hcd,xhci,ehci_hcd
scsi_mod              126725  6 firewire_sbp2,sr_mod,sg,sd_mod,usb_storage,libata
thermal                11674  0 
nls_base                6377  1 usbcore
thermal_sys            11942  2 processor,thermal

```

---


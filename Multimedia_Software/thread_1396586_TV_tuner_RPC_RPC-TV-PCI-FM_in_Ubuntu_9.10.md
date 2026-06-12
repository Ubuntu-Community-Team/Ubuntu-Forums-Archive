---
title: "TV tuner RPC RPC-TV-PCI-FM in Ubuntu 9.10"
date: 2010-02-02
forum: Multimedia Software
---

### Post by ioan_smid on 2010-02-02
How do I install a TV tuner RPC-TV-PCI-FM in Ubuntu 9.10?
I searched on various forums, but I do not found, how to set this model of tv tuner.
Thanks!

---

### Post by Jose Catre-Vandis on 2010-02-02
Please provide all product identification information from packaging/product and then run the following commands in a terminal and post output:
(assuming pci card plugged in)
```
sudo lspci -v
and
dmesg
```

---

### Post by ioan_smid on 2010-02-02
Thanks for kindness. Here are the data required.
Tvtuner is installed in the computer.
Information from product: Internal type, PCI,
 Connectivity:
 TV Input: 75 ohm type F or PH
FM input: 75 ohm
AV: RCA
S-Video 4 Pin Mini
Audio Jack for phone, 3.5 mm, Blue Audio output Jack phone 3.5 mm, Green
IR sensor input.
TV formats:
NTSC, PAL, SECAM
MPEG1 / 2.
FM radio reception: yes.
Remote control with multiple functions, depending on time-shifting, scheduling recordings.

**lspci result**
ioan@ioan-desktop:~$ sudo lspci -v
[sudo] password for ioan: 
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 8
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: [80] AGP version 3.5
    Capabilities: [50] Power Management version 2
    Kernel driver in use: agpgart-via
    Kernel modules: via-agp

00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller (prog-if 20)
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
    Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
    Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
    Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: [70] Power Management version 2
    Kernel modules: shpchp

00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-feafffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [68] Power Management version 2
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [88] HyperTransport: MSI Mapping Enable- Fixed+
    Capabilities: [98] Subsystem: VIA Technologies, Inc. Device c323
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [68] Power Management version 2
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [88] HyperTransport: MSI Mapping Enable- Fixed+
    Capabilities: [98] Subsystem: VIA Technologies, Inc. Device c323
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Subsystem: Device 1a7f:2004
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134
    Kernel modules: saa7134

00:0f.0 RAID bus controller: VIA Technologies, Inc. Device 7372
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    I/O ports at d000 [size=256]
    Capabilities: [c0] Power Management version 2
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 32
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at fc00 [size=16]
    Capabilities: [c0] Power Management version 2
    Kernel driver in use: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at c480 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at c800 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at c880 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at cc00 [size=32]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: uhci_hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20)
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at f9fff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Capabilities: [88] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: medium devsel
    Capabilities: [c0] Power Management version 2
    Kernel modules: i2c-viapro

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
    Subsystem: VIA Technologies, Inc. Device 337e
    Flags: bus master, medium devsel, latency 128
    Capabilities: [58] HyperTransport: Interrupt Discovery and Configuration

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
    Subsystem: Micro-Star International Co., Ltd. Device 387c
    Flags: bus master, medium devsel, latency 64, IRQ 23
    I/O ports at c000 [size=256]
    Memory at f9fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
    Flags: bus master, fast devsel, latency 0
    Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed+

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
    Subsystem: CardExpert Technology Device 0401
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at feae0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device 7387
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

**dmesg result**

[   19.966815] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966835] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966855] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966878] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966897] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966919] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966939] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966960] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.966980] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967001] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967024] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967042] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967065] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967086] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967107] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967128] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967148] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967169] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967190] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967211] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967232] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967252] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967273] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967294] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967315] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967336] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967357] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967377] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967398] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967419] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967440] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967461] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967482] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967503] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967523] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967544] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967565] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967585] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967606] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967627] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967649] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967670] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967691] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967710] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967732] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967752] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967774] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967794] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967816] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967836] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967857] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967877] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967899] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967918] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967941] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967961] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.967981] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   19.968017] hda-intel: spurious response 0x0:0x0, last cmd=0x370652
[   20.004109] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004126] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004152] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004167] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004224] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004228] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004250] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004254] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004271] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004292] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004312] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004333] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004354] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004375] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004396] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004417] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004437] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004458] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004479] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004500] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004521] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004541] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004562] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004583] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004604] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004625] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004646] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004667] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004687] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004708] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004729] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004750] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004771] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004791] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004813] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004833] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004854] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004874] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004895] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004916] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004937] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004958] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.004979] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005000] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005020] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005041] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005062] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005083] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005104] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005125] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005147] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005166] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005187] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005208] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005228] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005249] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005270] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005291] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005312] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005333] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005354] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005374] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005395] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005416] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005437] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005458] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005478] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005499] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005520] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005541] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005562] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005583] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005603] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005624] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005645] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005666] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005687] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005707] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005728] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005749] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005770] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005792] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005811] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005832] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005853] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005874] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005895] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005916] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005936] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005957] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005978] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.005999] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006022] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006040] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006062] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006082] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006103] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006124] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006144] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006167] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006186] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006207] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006228] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006249] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006269] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006290] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006311] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006333] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006353] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006374] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006395] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006416] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006436] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006457] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006478] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006499] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006519] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006540] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006561] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006582] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006603] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006624] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006644] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006665] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006686] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006707] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006728] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006749] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006770] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006790] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006811] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006831] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006852] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006873] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006894] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006915] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006936] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006957] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006978] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.006998] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007019] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007040] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007061] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007082] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007102] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007123] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007144] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007165] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007185] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007206] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007227] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007248] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007269] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007290] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007311] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007331] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007353] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007373] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007394] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007415] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007435] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007456] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007477] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007498] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007519] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007539] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007560] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007581] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007602] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007623] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.007644] hda-intel: spurious response 0x0:0x0, last cmd=0x570650
[   20.024076] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024094] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024114] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024135] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024156] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024177] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024197] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024218] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024239] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024260] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024281] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024302] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024323] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024343] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024364] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024385] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024406] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024427] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024447] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024468] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024489] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024509] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024531] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024551] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024572] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024593] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024614] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024635] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024656] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024677] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024698] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024719] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024740] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024760] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024781] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024801] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024822] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024843] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024864] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024884] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024905] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024926] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024947] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.024969] hda-intel: spurious response 0x0:0x0, last cmd=0x524015
[   20.025010] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025030] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025051] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025072] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025092] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025113] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025134] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025155] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025176] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025197] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025218] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025239] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025259] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025280] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025301] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025322] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025343] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025364] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025384] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025405] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025426] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025447] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025468] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025489] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025510] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025530] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025551] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025572] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025592] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025613] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025634] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025655] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025698] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025719] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025738] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025759] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025781] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025801] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025821] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025843] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025863] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025884] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025905] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025926] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025947] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025967] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.025988] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026009] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026030] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026051] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026071] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026092] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026113] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026134] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026155] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026176] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026197] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026218] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026238] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026259] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026280] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026301] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026322] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026343] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026363] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026384] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026404] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026425] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026446] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026467] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026488] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026509] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026530] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026551] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026593] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026613] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026634] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026655] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026675] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026697] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026716] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026737] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026758] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026779] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026800] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026821] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026841] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026863] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026883] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026904] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026925] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026946] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026967] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.026988] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027008] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027029] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027050] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027071] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027092] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027113] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027133] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027155] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027175] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027196] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027216] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027237] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027258] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027279] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027300] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027321] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027342] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027362] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027383] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027403] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027425] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027445] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027466] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027487] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027508] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027529] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027549] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027570] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027591] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027612] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027633] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027654] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027675] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027695] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.027716] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   20.560019] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   20.977201] CPU0 attaching NULL sched-domain.
[   20.977209] CPU1 attaching NULL sched-domain.
[   20.992094] CPU0 attaching sched-domain:
[   20.992100]  domain 0: span 0-1 level MC
[   20.992105]   groups: 0 1
[   20.992114] CPU1 attaching sched-domain:
[   20.992117]  domain 0: span 0-1 level MC
[   20.992121]   groups: 1 0
[   26.676021] eth0: no IPv6 routers present
[   46.792121] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792138] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792158] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792179] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792200] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792221] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792242] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792262] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792283] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792304] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792325] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792346] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792367] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792388] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792409] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792429] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792450] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792471] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792492] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792512] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792533] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792554] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792575] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792596] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792617] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792638] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792659] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792679] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792700] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792721] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792742] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792763] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792783] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792804] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792825] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792846] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792867] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792888] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792909] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792929] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792950] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792971] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.792992] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793013] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793034] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793055] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793076] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793096] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793117] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793138] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793159] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793179] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793200] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793221] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793242] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793263] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793284] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793305] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793326] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793347] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793367] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793388] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793409] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793430] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793450] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793471] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793492] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793513] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793534] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793555] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793576] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793596] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793617] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793638] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793659] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793680] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793701] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793722] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793742] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793763] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793784] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793805] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793826] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793846] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793867] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793888] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793909] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793930] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793951] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793972] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.793993] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794014] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794034] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794055] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794076] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794097] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794117] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794138] hda-intel: spurious response 0x0:0x0, last cmd=0x170503
[   46.794159] hda-intel: spurious response 0x0:0x0, last cmd=0x170503

**lspci result**
ioan@ioan-desktop:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. Device 7372
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237S PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

---

### Post by Jose Catre-Vandis on 2010-02-03
Well....this ia all I have learnt so far:
```
00:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

What is happening in your dmesg - looks like you have some issues with your sound card. I was hoping to see some information about your tv card either loading or not loading.

Also, please be specific about the brand and make and model of your card, the info you provided told me what it did not what it is.

---

### Post by ioan_smid on 2010-02-04
Thanks for the intention to help me. I gave up tvtuner.

---


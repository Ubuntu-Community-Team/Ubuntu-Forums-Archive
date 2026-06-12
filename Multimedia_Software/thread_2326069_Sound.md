---
title: "Sound"
date: 2016-05-28
forum: Multimedia Software
---

### Post by george110 on 2016-05-28
After reading through the threads I realise this is going to be difficult.
With all the ongoing updates to the latest version of Ubuntu dutifully installed I now find that there is no sound.
All I have to work with is the sound test on the VLC player which indicates that there is no sound.
When looking at tutorials that require access to sound I find I have none.
What would anyone do at this stage ?

---

### Post by T.J. on 2016-05-28
Could you please copy and paste your hardware list from a terminal?  You can get it using[I] lspci -vnn.

[/I]```
tj@Workstation:~$ lspci -vnn
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14]
    Flags: fast devsel
    Capabilities: <access denied>


00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
    Flags: fast devsel, IRQ 26
    Capabilities: <access denied>


00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fe500000-fe5fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:09.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port H) [1002:5a1c] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fe400000-fe4fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:0a.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx1 port A) [1002:5a1d] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe300000-fe3fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:0b.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (NB-SB link) [1002:5a1f] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fd000000-fe0fffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000b1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1458:b002]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
    I/O ports at f040 [size=8]
    I/O ports at f030 [size=4]
    I/O ports at f020 [size=8]
    I/O ports at f010 [size=4]
    I/O ports at f000 [size=16]
    Memory at fe60b000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe60a000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe609000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe608000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe607000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385]
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco


00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
    Subsystem: Gigabyte Technology Co., Ltd SBx00 Azalia (Intel HDA) [1458:a132]
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at fe600000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Flags: bus master, 66MHz, medium devsel, latency 0


00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fe200000-fe2fffff


00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe606000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1] (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: fe100000-fe1fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at fe605000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
    Subsystem: Gigabyte Technology Co., Ltd SB7x0/SB8x0/SB9x0 USB EHCI Controller [1458:5004]
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at fe604000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
    Flags: fast devsel
    Capabilities: <access denied>


00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
    Flags: fast devsel


00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Flags: fast devsel
    Kernel modules: amd64_edac_mod


00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp


00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
    Flags: fast devsel


01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Barts XT [Radeon HD 6870] [1002:6738] (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Barts XT [Radeon HD 6870] [1682:3108]
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe520000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fe500000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon


01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]
    Subsystem: XFX Pine Group Inc. Barts HDMI Audio [Radeon HD 6800 Series] [1682:aa88]
    Flags: fast devsel, IRQ 7
    Memory at fe540000 (64-bit, non-prefetchable) [disabled] [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd_hda_intel


02:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd EJ168 USB 3.0 Host Controller [1458:5007]
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at fe400000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


03:00.0 SATA controller [0106]: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller [1b4b:9172] (rev 11) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd 88SE9172 SATA 6Gb/s Controller [1458:b000]
    Flags: bus master, fast devsel, latency 0, IRQ 34
    I/O ports at d040 [size=8]
    I/O ports at d030 [size=4]
    I/O ports at d020 [size=8]
    I/O ports at d010 [size=4]
    I/O ports at d000 [size=16]
    Memory at fe310000 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at fe300000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci


04:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 960] [10de:1401] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. GM206 [GeForce GTX 960] [3842:2966]
    Flags: bus master, fast devsel, latency 0, IRQ 37
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at c000 [size=128]
    Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci
    Kernel modules: nvidiafb, nouveau


04:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:2966]
    Flags: bus master, fast devsel, latency 0, IRQ 38
    Memory at fe080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: vfio-pci
    Kernel modules: snd_hda_intel


05:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0) (prog-if 10 [OHCI])
    Subsystem: Gigabyte Technology Co., Ltd GA-7VT600-1394 Motherboard [1458:1000]
    Flags: bus master, medium devsel, latency 32, IRQ 22
    Memory at fe200000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at b000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci


06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Flags: bus master, fast devsel, latency 0, IRQ 32
    I/O ports at a000 [size=256]
    Memory at d0004000 (64-bit, prefetchable) [size=4K]
    Memory at d0000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


07:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd EJ168 USB 3.0 Host Controller [1458:5007]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at fe100000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd
```

It could be anything: simply muted, bad driver, etc.  The readout will help diagnose the problem.

---

### Post by Yellow Pasque on 2016-05-28
Did you ever have sound?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by george110 on 2016-05-28
Thank you for responding. Here is what came up with * lspci -vnn.*

george@george-pc:~$ lspci -vnn.
lspci: invalid option -- '.'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>][:<class>]        Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
george@george-pc:~$

---

### Post by george110 on 2016-05-28
Yes, once upon a time I had sound.

---

### Post by Yellow Pasque on 2016-05-28
I assume you're working on getting that ALSA info ;) [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by george110 on 2016-05-28
That's a really big file & it doesn't copy & paste well. There are issues with it as in somethings are missing & so on

---

### Post by Yellow Pasque on 2016-05-29
Use  [ code ][ /code ] tags (no spaces).

---

### Post by T.J. on 2016-05-29
Well, can you tell me what kind of audio hardware you have and what driver it is using?  That is the main question.  After we know that, we can check other things.

If you had sound and now do not, you can check a few things.  Make sure that the audio is not muted.

---


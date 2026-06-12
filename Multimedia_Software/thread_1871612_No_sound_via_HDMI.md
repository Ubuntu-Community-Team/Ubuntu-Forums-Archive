---
title: "No sound via HDMI"
date: 2011-10-29
forum: Multimedia Software
---

### Post by Red Kelly on 2011-10-29
Hi I am stumped as what to do next I have done every tutorial and worked through all the suggestions else where but still nothing.

**sudo aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

**sudo lspci -v**
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: e0000000-f30fffff
    Capabilities: [88] Subsystem: Samsung Electronics Co Ltd Device c06a
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f7c08000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7c00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f6800000-f7bfffff
    Prefetchable memory behind bridge: 00000000f7d00000-00000000f7efffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c06a
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=05, sec-latency=0
    I/O behind bridge: 00007000-0000afff
    Memory behind bridge: f3200000-f53fffff
    Prefetchable memory behind bridge: 00000000fc000000-00000000fc1fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c06a
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f5400000-f67fffff
    Prefetchable memory behind bridge: 00000000fc200000-00000000fc3fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c06a
    Capabilities: [a0] Power Management version 2
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7c07000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Capabilities: [98] PCI Advanced Features
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    Capabilities: [50] Subsystem: Gammagraphx, Inc. (or missing ID) Device 0000

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 45
    I/O ports at e070 [size=8]
    I/O ports at e060 [size=4]
    I/O ports at e050 [size=8]
    I/O ports at e040 [size=4]
    I/O ports at e020 [size=32]
    Memory at f7c06000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Capabilities: [b0] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: medium devsel, IRQ 3
    Memory at f7c05000 (64-bit, non-prefetchable) [size=256]
    I/O ports at e000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f7c04000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel ips
    Kernel modules: intel_ips

01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at d000 [size=128]
    [virtual] Expansion ROM at f3000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f3080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e025
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f6800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
    Subsystem: Samsung Electronics Co Ltd Device c06a
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f5420000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at b000 [size=256]
    Expansion ROM at f5400000 [disabled] [size=128K]
    Capabilities: [48] Power Management version 3
    Capabilities: [5c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [c0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [130] Device Serial Number 5f-c2-42-ff-ff-54-24-00
    Kernel driver in use: sky2
    Kernel modules: sky2

3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Intel Corporation Device 8086
    Flags: bus master, fast devsel, latency 0

```

All the volume indercators show that it should be playing sound but nothing comes out.

Anyone have any ideas? I have run out of places to look.

I'm using Ubuntu 10.10

---

### Post by MasterZ on 2011-10-29
Hi,

I wrote a guide some time ago to make my NVIDIA HDMI work. 
Maybe you can try those steps:

[http://ubuntuforums.org/showthread.php?t=1720294](http://ubuntuforums.org/showthread.php?t=1720294)

MasterZ.

---

### Post by Red Kelly on 2011-10-29
Thanks, but still no luck.
None of the audio devices in vlc worked (execept 0.0 out of the laptop speekers)
I know the cable and TV work because when I boot to windows it switch and works fine.

---

### Post by Red Kelly on 2011-10-29
Success, I didn't realise I had to have the video going out to get the audio to work.
Thanks for your help.

---


---
title: "No Sound from Speakers and Audio Jack"
date: 2019-06-17
forum: Multimedia Software
---

### Post by jproberge2 on 2019-06-17
Hello to all, 

I think at this point, I badly need help. I spent more than 24 hours full time trying to get sound from my laptop, but to no avail. My Ubuntu version is 18.04 (but I've also tried Ubuntu 19.04 which gives the same results), and I've setup a dual-boot with windows 10. Speakers and audio jack work totally fine under Windows 10, but they never work with Ubuntu.

Here are more information about my setup:

1) My ALSA information is located [here]("http://alsa-project.org/db/?f=bcdf5c8be31ce8b9e848a29ef292e9125f26def0")

2) The output of "inxi -Fx":

```
System:    Host: JP Kernel: 4.18.0-22-generic x86_64 bits: 64 gcc: 7.3.0 Desktop: Gnome 3.28.4 (Gtk 2.24.32)
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: Notebook product: P95_96_97Ex Rx serial: N/A
           Mobo: Notebook model: P95_96_97Ex Rx serial: N/A UEFI: INSYDE v: 1.07.08P date: 05/07/2019
Battery    BAT0: charge: 58.6 Wh 100.0% condition: 58.6/56.2 Wh (104%) model: Notebook BAT status: Full
           hidpp__0: charge: N/A condition: NA/NA Wh model: Logitech M215 status: Discharging
CPU:       6 core Intel Core i7-8750H (-MT-MCP-) arch: Skylake rev.10 cache: 9216 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 26496
           clock speeds: max: 4100 MHz 1: 1723 MHz 2: 3261 MHz 3: 3257 MHz 4: 3205 MHz 5: 3302 MHz 6: 3068 MHz
           7: 3664 MHz 8: 2921 MHz 9: 3309 MHz 10: 3240 MHz 11: 3201 MHz 12: 3220 MHz
Graphics:  Card-1: Intel UHD Graphics 630 (Mobile) bus-ID: 00:02.0
           Card-2: NVIDIA TU106M [GeForce RTX 2070 Mobile] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.20.1 ) drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@144.01hz
           OpenGL: renderer: GeForce RTX 2070 with Max-Q Design/PCIe/SSE2
           version: 4.6.0 NVIDIA 410.104 Direct Render: Yes
Audio:     Card-1 Intel Cannon Lake PCH cAVS driver: snd_hda_intel bus-ID: 00:1f.3
           Card-2 NVIDIA TU106 High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.18.0-22-generic
Network:   Card-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi bus-ID: 00:14.3
           IF: wlp0s20f3 state: up mac: d0:c6:37:d9:65:98
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 08:00.0
           IF: enp8s0 state: down mac: 80:fa:5b:67:ac:bb
Drives:    HDD Total Size: 500.1GB (7.1% used)
           ID-1: /dev/nvme0n1 model: WDC_WDS500G1B0C size: 500.1GB
Partition: ID-1: / size: 236G used: 29G (13%) fs: ext4 dev: /dev/nvme0n1p5
           ID-2: swap-1 size: 5.25GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 63.0C mobo: N/A gpu: 0.0:45C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 369 Uptime: 1:19 Memory: 2408.5/15876.1MB Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56
```

3) The output of "aplay -l":

```
**** List of PLAYBACK Hardware Devices ****card 0: PCH [HDA Intel PCH], device 0: ALC1220 Analog [ALC1220 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1220 Digital [ALC1220 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

4) The output of "sudo lspci -v" :
```
[sudo] password for jproberge: 00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: a0000000-b40fffff
    Prefetchable memory behind bridge: 00000000b4100000-00000000b41fffff
    Capabilities: [88] Subsystem: CLEVO/KAPOK Computer Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] #19
    Kernel driver in use: pcieport


00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0, IRQ 160
    Memory at b5000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)
    Kernel driver in use: i915
    Kernel modules: i915


00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
    Subsystem: CLEVO/KAPOK Computer Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b4610000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device


00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b4624000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal


00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10) (prog-if 30 [XHCI])
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, medium devsel, latency 0, IRQ 127
    Memory at b4600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: xhci_hcd


00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0
    Memory at b4620000 (64-bit, non-prefetchable) [size=8K]
    Memory at b4625000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3


00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
    Subsystem: Intel Corporation Device 0034
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b4618000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [80] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] #00
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [164] Vendor Specific Information: ID=0010 Rev=0 Len=014 <?>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 8f800000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci


00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 8f801000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci


00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0, IRQ 145
    Memory at b4628000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [a4] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:17.0 SATA controller: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 129
    Memory at b4622000 (32-bit, non-prefetchable) [size=8K]
    Memory at b462c000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5080 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5060 [size=32]
    Memory at b462b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci


00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #21 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 95e1
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport


00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    Memory behind bridge: b4500000-b45fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 95e6
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport


00:1d.6 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #15 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: b4400000-b44fffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 95e6
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [220] #19
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport


00:1d.7 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #16 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    Memory behind bridge: b4300000-b43fffff
    Capabilities: [40] Express Root Port (Slot-), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 95e6
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [200] L1 PM Substates
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport


00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, medium devsel, latency 0


00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at b461c000 (64-bit, non-prefetchable) [size=16K]
    Memory at b4200000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: medium devsel, IRQ 255
    Memory at b4629000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel modules: i2c_i801


00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
    Subsystem: CLEVO/KAPOK Computer Device 95e6
    Flags: bus master, fast devsel, latency 0
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]


01:00.0 VGA compatible controller: NVIDIA Corporation TU106M [GeForce RTX 2070 Mobile] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 95e1
    Flags: bus master, fast devsel, latency 0, IRQ 162
    Memory at b3000000 (32-bit, non-prefetchable) [size=16M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    [virtual] Expansion ROM at b2000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [420] Advanced Error Reporting
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Capabilities: [bb0] #15
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia


01:00.1 Audio device: NVIDIA Corporation TU106 High Definition Audio Controller (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device 95e1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at b4000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


01:00.2 USB controller: NVIDIA Corporation TU106 USB 3.1 Host Controller (rev a1) (prog-if 30 [XHCI])
    Subsystem: NVIDIA Corporation Device 0000
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at b4100000 (64-bit, prefetchable) [size=256K]
    Memory at b4140000 (64-bit, prefetchable) [size=64K]
    Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Kernel driver in use: xhci_hcd


01:00.3 Serial bus controller [0c80]: NVIDIA Corporation TU106 USB Type-C Port Policy Controller (rev a1)
    Subsystem: NVIDIA Corporation Device 0000
    Flags: fast devsel, IRQ 255
    Memory at b4004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Power Management version 3
    Capabilities: [100] Advanced Error Reporting


07:00.0 Non-Volatile memory controller: Sandisk Corp WD Black 2018/PC SN520 NVMe SSD (rev 01) (prog-if 02 [NVM Express])
    Subsystem: Sandisk Corp WD Black 2018/PC SN520 NVMe SSD
    Flags: bus master, fast devsel, latency 0, IRQ 16, NUMA node 0
    Memory at b4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [b0] MSI-X: Enable+ Count=17 Masked-
    Capabilities: [c0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [150] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [1b8] Latency Tolerance Reporting
    Capabilities: [300] #19
    Capabilities: [900] L1 PM Substates
    Kernel driver in use: nvme
    Kernel modules: nvme


08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: CLEVO/KAPOK Computer RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at 3000 [size=256]
    Memory at b4404000 (64-bit, non-prefetchable) [size=4K]
    Memory at b4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable+ Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169


09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
    Subsystem: CLEVO/KAPOK Computer RTS525A PCI Express Card Reader
    Flags: bus master, fast devsel, latency 0, IRQ 130
    Memory at b4300000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [148] Device Serial Number 00-00-00-01-00-4c-e0-00
    Capabilities: [158] Latency Tolerance Reporting
    Capabilities: [160] L1 PM Substates
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
```

5) The output of "sudo lshw -numeric -c multimedia":

```
  *-multimedia                     description: Audio device
       product: TU106 High Definition Audio Controller [10DE:10F9]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:17 memory:b4000000-b4003fff
  *-usb:1
       description: Video
       product: BisonCam, NB Pro [5986:112D]
       vendor: Bison [5986]
       physical id: 8
       bus info: usb@1:8
       version: 6.09
       serial: 200901010001
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia
       description: Audio device
       product: Cannon Lake PCH cAVS [8086:A348]
       vendor: Intel Corporation [8086]
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:16 memory:b461c000-b461ffff memory:b4200000-b42fffff 
```

6) The output of "cat /proc/asound/card0/codec* | grep Codec":
```
Codec: Realtek ALC1220Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec1220
Subsystem Id: 0x155895e6
Revision Id: 0x100003
No Modem Function Group found
Default PCM:
N/A
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power: setting=UNKNOWN, actual=UNKNOWN, Error, Clock-stop-OK, Setting-reset
Invalid AFG subtree
Codec: Intel Kabylake HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x8086280b
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
N/A
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power: setting=UNKNOWN, actual=UNKNOWN, Error, Clock-stop-OK, Setting-reset
Invalid AFG subtree

```

I obviously think this might not be normal, especially the "Invalid AFG subtree" and error messages. So far I've tried a lot of different things:

1) I've tried all the steps from the "[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")"
1) I've tried installing the "oem-audio-hda-daily-dkms" package;
2) I've tried to install/remove/reinstall alsa-base, alsa-utils, pulseaudio, pavucontrol many times
3) I've played with the options in the file /etc/modprobe.d/alsa-base.conf:
   a) I've tried to add "options snd-hda-intel model=auto"  and I also tried different models: auto, clevo, laptop-eapd, clevo m-720, generic, basic and even z71v position_fix=1.
4) I've tried adding : ```
[General]
description = Headphones + Digital Output (S/PDIF)

``` in the file "/usr/share/pulseaudio/alsa-mixer/paths/iec958-stereo-output.conf"
5) I've even tried a live USB stick with Ubuntu 19.04 (after reading somewhere that this was fixed on 19.04)

But I never was able to get sound from the speakers or the audio jack output, in fact everything else work (keyboard backlights, RTX2070 drivers, etc...) except sound... Anyone has an idea / tip / or anything to make my speakers and audio jack work on my computer?

---

### Post by jproberge2 on 2019-06-19
[SIZE=3]This is solved now! Wow, I spent way too much time working on this... So anyway, here is what I've done to solve the problem:[/SIZE]

[SIZE=2]1) First of all, by looking at the output of "cat /proc/asound/card0/codec*" it was obvious something  was wrong... So first to fix that I had to edit the file "/etc/modprobe.d/alsa-base.conf" to add the line:  "options snd-hda-intel probe_mask=0x1" . After reboot, then I could see everything the output of "cat /proc/asound/card0/codec*" that was looking perfect but still no sound. At least, things had improved a little bit now;

2) As shown by the output of "cat /proc/asound/card0/codec* | grep Codec", my HD Audio Codec is ALC1220 so I went [here]("https://www.infradead.org/~mchehab/rst_conversion/sound/hd-audio/models.html") to look at what specific model that corresponded. My laptop is a clevo laptop ("clevo-p950", in the list), so I added the line "options snd-hda-intel model=clevo-p950" to the the "/etc/modprobe.d/alsa-base.conf" file and rebooted. I thought I had solved it at this point but.... nope, still no sound from the speakers or the headphones... but then;

3) After I posted a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1833161"), someone suggested that I upgrade my kernel version to at least 5.0. So if you are in this situation where you think you should proceed with a kernel upgrade and it's your first time, don't worry, it's not hard to do at all. I used to build my kernel from source (which can be a long process depending on your machine) but now there's a nice GUI and debian packages to help you out, this tool is Ukuu, see [this article]("https://www.addictivetips.com/ubuntu-linux-tips/get-the-latest-linux-kernel-version-in-ubuntu/") for example... In my case and at this moment of writing, after a fresh Ubuntu 18.04 install and update, the kernel version was [COLOR=#333333][FONT=monospace]4.18.0-22 [/FONT][/COLOR]which was not able to make the "clevo-p950" option work. So I upgraded my kernel to 5.0.2, rebooted and everything started to work! Now my microphone, my headphone and my speakers are all working. This is nice! I hope this can help somebody! Good luck![/SIZE]

---

### Post by agentefilemonpi on 2020-05-03
> **jproberge2 said:**
> [SIZE=3]This is solved now! Wow, I spent way too much time working on this... So anyway, here is what I've done to solve the problem:[/SIZE]


I have registered just to thank you for sharing your solution. I had the same problem with 20.04 after using the NVIDIA drivers. Nouveau would display just a black screen. It was a choice between either having no audio and being able to use the external monitor, or having audio and no external monitor.

With 20.04 as it is on a newer kernel just adding the entries you mentioned in 

/etc/modprobe.d/alsa-base.conf

brought the sound on the headphones. Adding the second part with the model made the audio work as before. So for 20.04 adding the the below to alsa-base.conf made it work for me:

# Manual entry to allow audio via headphones because NVIDIA drivers break the built-in audio
options snd-hda-intel model=clevo-p950
options snd-hda-intel probe_mask=0x1

I had opened a [bug yesterday]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1876499?comments=all") and spent two days working on this and was about to give up.

Thank you so so so so so much. :)

---


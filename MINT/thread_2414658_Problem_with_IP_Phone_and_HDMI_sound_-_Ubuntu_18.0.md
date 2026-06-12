---
title: "Problem with IP Phone and HDMI sound - Ubuntu 18.04, kernel 4.15"
date: 2019-03-13
forum: MINT
---

### Post by jma-kinho on 2019-03-13
Hi, I have a BIG problem with the kernels and drivers on thin clients.
Where I work, I share the wireless from the thin client to the IP phones by the ethernet port. I have Thin clients with hardware a little old that works everything on linux mint 18 (ubuntu 16.04, kernel 4.4). But, I have another new thin clients with had problems on boot (freeze screen) with linux mint 18. So, I upgraded them to linux mint 19.1 (ubuntu 18.04, kernek 4.15). But other problems appeared. The Ip phone doesnt work on them. I can make a call, I listen the person on the other side, but the person doesnt listen me. I can make calls, but I dont receive. I read many forums but nothing helps me. So, I made a test and I had note that the phone worked in distros with kernel 4.4. In kernel 4.8 or above, the phone didnt work. So I installed the kernel 4.4.174 on linux mint 19.1 and the problem with the phone was solved. Buuuut, one more time, another problem appeared. I have some thin clients connected on TVs. So, when I use the HDMI port, the video is ok, but no sound. I made a test with the olders thin clients and works fine with the kernel 4.4. But, with the new ones, the sound only works on kernel 4.15. I tried everyting that I had read, (change things on the alsa, mixer, EVERYTHIN), but the HDMI sound only works on kernel 4.10 or above. 
SO, my problem is: I need everything working on the new ones. But, if the IP phones works, HDMI sound doesnt work and vice versa. 
if its possible, I would want more help to solve the HDMI problem. But, if possible to solve the IP Phone problem on kernel 4.15, I will apreciate so much.

The hardware config from the new thin client with kernel 4.4.174 below

```
lspci -v

00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge (rev 0b)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge
    Flags: bus master, fast devsel, latency 0


00:02.0 VGA compatible controller: Intel Corporation Device 5a85 (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: Elitegroup Computer Systems Device 9cc7
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [40] Vendor Specific Information: Len=0c <?>
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [ac] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [100] Process Address Space ID (PASID)
    Capabilities: [200] Address Translation Service (ATS)
    Capabilities: [300] Page Request Interface (PRI)
    Kernel modules: i915


00:0e.0 Audio device: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster (rev 0b) (prog-if 80)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster
    Flags: bus master, fast devsel, latency 32, IRQ 129
    Memory at 91410000 (64-bit, non-prefetchable) [size=16K]
    Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine
    Flags: bus master, fast devsel, latency 0, IRQ 127
    Memory at 9141f000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [a4] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: mei_me
    Kernel modules: mei_me


00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b) (prog-if 01 [AHCI 1.0])
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 124
    Memory at 91414000 (32-bit, non-prefetchable) [size=8K]
    Memory at 9141c000 (32-bit, non-prefetchable) [size=256]
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f060 [size=32]
    Memory at 9141b000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci


00:13.0 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #1 (rev fb) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 120
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: 91300000-913fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [140] Access Control Services
    Capabilities: [150] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:13.1 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #2 (rev fb) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 121
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: 91200000-912fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [140] Access Control Services
    Capabilities: [150] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:13.2 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #3 (rev fb) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: 91100000-911fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] #00
    Capabilities: [140] Access Control Services
    Capabilities: [150] #00
    Capabilities: [200] L1 PM Substates
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b) (prog-if 30 [XHCI])
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI
    Flags: bus master, medium devsel, latency 0, IRQ 123
    Memory at 91400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: xhci_hcd


00:1a.0 Serial bus controller [0c80]: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PWM Pin Controller (rev 0b)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series PWM Pin Controller
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at 9141a000 (64-bit, non-prefetchable) [size=4K]
    Memory at 91419000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: pwm-lpss
    Kernel modules: pwm_lpss_pci


00:1c.0 SD Host controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller (rev 0b) (prog-if 01)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series eMMC Controller
    Flags: bus master, fast devsel, latency 0, IRQ 39
    Memory at 91418000 (64-bit, non-prefetchable) [size=4K]
    Memory at 91417000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci


00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface
    Flags: bus master, medium devsel, latency 0


00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)
    Subsystem: Elitegroup Computer Systems Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller
    Flags: medium devsel, IRQ 255
    Memory at 91416000 (64-bit, non-prefetchable) [size=256]
    I/O ports at f040 [size=32]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801


01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Elitegroup Computer Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 125
    I/O ports at e000 [size=256]
    Memory at 91304000 (64-bit, non-prefetchable) [size=4K]
    Memory at 91300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169


02:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
    Subsystem: Intel Corporation Dual Band Wireless AC 3165
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at 91200000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number ac-ed-5c-ff-ff-fc-b9-df
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [154] L1 PM Substates
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Elitegroup Computer Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 126
    I/O ports at d000 [size=256]
    Memory at 91104000 (64-bit, non-prefetchable) [size=4K]
    Memory at 91100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Capabilities: [170] Latency Tolerance Reporting
    Capabilities: [178] L1 PM Substates
    Kernel driver in use: r8169
    Kernel modules: r8169



-------------------------------------------------------------------------------------------------------------------------------------
PS:
I only had note a diference on the IRQ number in the audio device with kernel 4.15. It was like this:

Flags: bus master, fast devsel, latency 32, IRQ 130
    Memory at 91410000 (64-bit, non-prefetchable) [size=16K]
    Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl
```

I don't know if this is something wrong, but it can helps.

Thank you so much for any help and sorry for my bad english, I'm a brazilian guy

---

### Post by DuckHook on 2019-03-13
*Thread moved to **MINT** as the more appropriate forum.*

---


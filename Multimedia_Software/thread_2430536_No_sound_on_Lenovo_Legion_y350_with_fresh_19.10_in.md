---
title: "No sound on Lenovo Legion y350 with fresh 19.10 install"
date: 2019-11-03
forum: Multimedia Software
---

### Post by aroswald19772 on 2019-11-03
I upgraded from 19.04 to 19.10 as soon as it was released, only to find everything working except my sound. after fighting with the issue, trying any solution i could find on the internet, messing up bluetooth, and generally wiping out and reinstalling alsa, pulse audio, and changing conf files, i decided to do a fresh 19.10 install to see if it was a problem with the update.

I still have no audio input or output.

```

root@OzNet3:/home/alexandra# lspci -v
00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
    Subsystem: Lenovo 8th Gen Core Processor Host Bridge/DRAM Registers
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=10 <?>
    Kernel driver in use: skl_uncore

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff [size=4K]
    Memory behind bridge: a3000000-a40fffff [size=17M]
    Prefetchable memory behind bridge: 0000000090000000-00000000a1ffffff [size=288M]
    Capabilities: [88] Subsystem: Lenovo Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
    Capabilities: [80] Power Management version 3
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [a0] Express Root Port (Slot+), MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [140] Root Complex Link
    Capabilities: [d94] Secondary PCI Express <?>
    Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile) (prog-if 00 [VGA controller])
    Subsystem: Lenovo UHD Graphics 630 (Mobile)
    Flags: bus master, fast devsel, latency 0, IRQ 143
    Memory at a2000000 (64-bit, non-prefetchable) [size=16M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
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
    Subsystem: Lenovo Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a4310000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device

00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
    Subsystem: Lenovo Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at a4324000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [dc] Power Management version 2
    Capabilities: [f0] PCI Advanced Features

00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Thermal Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a4325000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal

00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10) (prog-if 30 [XHCI])
    Subsystem: Lenovo Cannon Lake PCH USB 3.1 xHCI Host Controller
    Flags: bus master, medium devsel, latency 0, IRQ 125
    Memory at a4300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: xhci_hcd

00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Shared SRAM
    Flags: bus master, fast devsel, latency 0
    Memory at a4320000 (64-bit, non-prefetchable) [size=8K]
    Memory at a4326000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3

00:14.3 Network controller: Intel Corporation Wireless-AC 9560 [Jefferson Peak] (rev 10)
    Subsystem: Intel Corporation Wireless-AC 9560 [Jefferson Peak]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a4318000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [40] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [80] MSI-X: Enable+ Count=16 Masked-
    Capabilities: [100] Null
    Capabilities: [14c] Latency Tolerance Reporting
    Capabilities: [164] Vendor Specific Information: ID=0010 Rev=0 Len=014 <?>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

00:15.0 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #0 (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Serial IO I2C Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    [virtual] Memory at 8fc00000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:15.1 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH Serial IO I2C Controller #1 (rev 10)
    Subsystem: Lenovo Cannon Lake PCH Serial IO I2C Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    [virtual] Memory at 8fc01000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
    Subsystem: Lenovo Cannon Lake PCH HECI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 128
    Memory at a4329000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 3
    Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [a4] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Cannon Lake Mobile PCH SATA AHCI Controller (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Cannon Lake Mobile PCH SATA AHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 126
    Memory at a4322000 (32-bit, non-prefetchable) [size=8K]
    Memory at a432e000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 5080 [size=8]
    I/O ports at 5088 [size=4]
    I/O ports at 5060 [size=32]
    Memory at a432d000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00006000-00006fff [size=4K]
    Memory behind bridge: 8f800000-8f9fffff [size=2M]
    Prefetchable memory behind bridge: 000000008fa00000-000000008fbfffff [size=2M]
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Illegal Vendor ID Cannon Lake PCH PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Kernel driver in use: pcieport

00:1d.5 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #14 (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 124
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00003fff [size=4K]
    Memory behind bridge: a4200000-a42fffff [size=1M]
    Prefetchable memory behind bridge: None
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo Cannon Lake PCH PCI Express Root Port
    Capabilities: [a0] Power Management version 3
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Access Control Services
    Capabilities: [150] Precision Time Measurement
    Capabilities: [200] L1 PM Substates
    Capabilities: [220] Secondary PCI Express <?>
    Capabilities: [250] Downstream Port Containment
    Kernel driver in use: pcieport

00:1e.0 Communication controller: Intel Corporation Device a328 (rev 10)
    Subsystem: Lenovo Device 380f
    Flags: bus master, fast devsel, latency 0, IRQ 20
    [virtual] Memory at 8fc02000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: [80] Power Management version 3
    Capabilities: [90] Vendor Specific Information: Len=14 <?>
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci

00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
    Subsystem: Lenovo Device 3810
    Flags: bus master, medium devsel, latency 0

00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
    Subsystem: Lenovo Cannon Lake PCH cAVS
    Flags: bus master, fast devsel, latency 32, IRQ 144
    Memory at a431c000 (64-bit, non-prefetchable) [size=16K]
    Memory at a4100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [50] Power Management version 3
    Capabilities: [80] Vendor Specific Information: Len=14 <?>
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl, sof_pci_dev

00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
    Subsystem: Lenovo Cannon Lake PCH SMBus Controller
    Flags: medium devsel, IRQ 16
    Memory at a432b000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5040 [size=32]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801

00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
    Subsystem: Lenovo Cannon Lake PCH SPI Controller
    Flags: bus master, fast devsel, latency 0
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 3000 [size=256]
    Memory at a4204000 (64-bit, non-prefetchable) [size=4K]
    Memory at a4200000 (64-bit, non-prefetchable) [size=16K]
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

```

Sound settings list only Dummy output, with nothing to switch to.

My assumption is that it is picking up the nvidia driver which only outputs to HDMI.

If i cant find a solution for this problem, I'm going back to 19.04. Everything worked perfectly before the update. Any help is greatly appreciated.

---

### Post by aroswald19772 on 2019-11-03
After a reboot, it started working again as mysteriously as it stopped, I have no idea what i did except alist -l.

---

### Post by mörgæs on 2019-11-03
Good, please mark the thread solved.

---


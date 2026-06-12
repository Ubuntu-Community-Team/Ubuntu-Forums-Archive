---
title: "How to fix Tearing?"
date: 2016-11-24
forum: Multimedia Software
---

### Post by alxvu on 2016-11-24
Hi! How to fix Tearing? ubuntu 16.04, intel (hd graphics 4600) + nvidia (geforce 840m).

---

### Post by ajgreeny on 2016-11-24
What driver are you using for that graphic card as you may need the proprietary nvidia version?
Let's see the output of ```
lspci -k
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by alxvu on 2016-11-24
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
    DeviceName: Realtek(R) RTL-8111GA Gigabit Network Connection
    Subsystem: Acer Incorporated [ALI] 4th Gen Core Processor DRAM Controller
    Kernel driver in use: hsw_uncore
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
    DeviceName: Intel(R) HD Graphics
    Subsystem: Acer Incorporated [ALI] Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
    Subsystem: Acer Incorporated [ALI] Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family USB xHCI
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family MEI Controller
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family USB EHCI
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    DeviceName: Realtek High Definition Audio
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset High Definition Audio Controller
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family USB EHCI
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
    Subsystem: Acer Incorporated [ALI] C220 Series Chipset Family H81 Express LPC Controller
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
    DeviceName: Intel(R) 8 Series SATA AHCI Controller
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
    Subsystem: Acer Incorporated [ALI] 8 Series/C220 Series Chipset Family SMBus Controller
    Kernel modules: i2c_i801
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
    Subsystem: Acer Incorporated [ALI] GM108M [GeForce 840M]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_367, nvidia_367_drm
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Kernel driver in use: r8169
    Kernel modules: r8169
20:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
    Subsystem: AzureWave QCA9565 / AR9565 Wireless Network Adapter
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

---

### Post by mc4man on 2016-11-24
Simple on an ubuntu session (unity/compiz), just use the Intel gpu
If wanting no tearing on nvidia drivers via nvidia-prime you can wait till 17.04 gets xserver 1.19 or wait until 16.04.3 image comes out (a year or so.

---

### Post by binamenator on 2016-11-24
I don't see how your graphics card should matter, couldn't you just use compton?

---


---
title: "you tube and most other video crashing"
date: 2013-02-26
forum: Multimedia Software
---

### Post by gn2tx on 2013-02-26
Every time I try and watch a video Ubuntu freezes and I have to reboot. I tried reinstalling Ubuntu but its still not fixed.

---

### Post by carl4926 on 2013-02-26
Could be you need to install a proprietary graphics driver.
What GPU do you have?

---

### Post by gn2tx on 2013-02-26
The driver is installed, system says its a VESA: RS780
Now I'm getting error messages telling me to check for updates and an error every time I do so.

---

### Post by carl4926 on 2013-02-26
> **gn2tx said:**
> The driver is installed, system says its a VESA: RS780
Now I'm getting error messages telling me to check for updates and an error every time I do so.

Vesa is a very basic driver

Please post result of
```
lspci -nnk
```

---

### Post by gn2tx on 2013-02-26
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ee]
00:01.0 PCI bridge [0604]: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) [1043:9602]
    Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ohci_hcd
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ohci_hcd
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ehci_hcd
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ohci_hcd
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3a)
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ea]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82ef]
    Kernel driver in use: ohci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780C [Radeon HD 3100] [1002:9611]
    Subsystem: ASUSTeK Computer Inc. Device [1043:82ee]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard [1043:82c6]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by carl4926 on 2013-02-26
Do you have hybrid graphics
It looks like it

---

### Post by gn2tx on 2013-02-26
I don't know

---


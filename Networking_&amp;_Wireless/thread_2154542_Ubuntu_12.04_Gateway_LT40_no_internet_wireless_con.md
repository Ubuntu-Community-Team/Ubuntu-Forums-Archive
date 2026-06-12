---
title: "Ubuntu 12.04 Gateway LT40 no internet wireless connection"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by tikygaki on 2013-06-15
Hi everyone!

I recently installed Ubuntu 12.04 in my netbook Gateway LT4003m with Intel Atom N2600.

My wireless doesn't works, I can only connect by ethernet.

Plis, help me!

---

### Post by carl4926 on 2013-06-15
Let us see the result of

```
lspci -nnk
```

---

### Post by tikygaki on 2013-06-15
> **carl4926 said:**
> Let us see the result of

```
lspci -nnk
```

Hi!

lspci -nnk

```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf1] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: gma500
    Kernel modules: gma500_gfx
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e042]
    Kernel driver in use: wl
    Kernel modules: wl, bcma
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0624]
    Kernel driver in use: rtsx_pci
    Kernel modules: rts_pstor, rtsx_pci

```

---

### Post by ahallubuntu on 2013-06-15
~

---


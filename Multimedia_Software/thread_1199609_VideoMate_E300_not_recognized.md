---
title: "VideoMate E300 not recognized"
date: 2009-06-29
forum: Multimedia Software
---

### Post by MarcoFranzoso on 2009-06-29
Hello All

I cant seem to get my tv card to work. I have installed TVtime and MeTv but neither work.....for TVtime this is what it says:No such file or directory. Cannot open capture device /dev/video0.....and for MeTv: There are no available DVB tuner devices

When I do a lspci this is what it says:

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)

When I do a dmesg this is what it says:

[   17.047852] Linux video capture interface: v2.00
[   17.066562] cx23885 driver version 0.0.1 loaded
[   17.066869] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 17
[   17.066876] cx23885 0000:03:00.0: PCI INT A -> Link[LNEB] -> GSI 17 (level, low) -> IRQ 17
[   17.066880] cx23885[0]: Your board isn't known (yet) to the driver.
[   17.066881] cx23885[0]: Try to pick one of the existing card configs via
[   17.066882] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   17.066883] cx23885[0]: version might help as well.
[   17.066885] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   17.066887] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   17.066888] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   17.066890] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   17.066892] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   17.066893] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   17.066895] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   17.066897] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   17.066898] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   17.066900] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   17.066901] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   17.066903] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   17.066905] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   17.066907] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   17.067119] CORE cx23885[0]: subsystem: 185b:e800, board: UNKNOWN/GENERIC [card=0,autodetected]
[   17.192963] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   17.192969] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xfe800000
[   17.192974] cx23885 0000:03:00.0: setting latency timer to 64


Any help would be greatly appreciated
thanx marco

---


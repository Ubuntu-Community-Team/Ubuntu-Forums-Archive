---
title: "HVR-4000  not loading firmware?"
date: 2010-05-21
forum: Multimedia Software
---

### Post by MMoudry on 2010-05-21
Hi,
My HVR-4000 works although not very good. I have the latest mythbuntu 10.04 and I compiled the V4L with the patch since the stock module is broken. Since then (or before I get this in messages), the firmware never gets loaded :

ay 21 11:37:44 socrates kernel: [   16.684339] Linux video capture interface: v2.00
May 21 11:37:44 socrates kernel: [   16.684530] ppdev: user-space parallel port driver
May 21 11:37:44 socrates kernel: [   16.694205] EDAC amd64_edac:  Ver: 3.2.0 Apr 28 2010
May 21 11:37:44 socrates kernel: [   16.699340] ip_tables: (C) 2000-2006 Netfilter Core Team
May 21 11:37:44 socrates kernel: [   16.711093] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
May 21 11:37:44 socrates kernel: [   16.719208] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
May 21 11:37:44 socrates kernel: [   16.726868] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
May 21 11:37:44 socrates kernel: [   16.727463] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
May 21 11:37:44 socrates kernel: [   16.727465] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
May 21 11:37:44 socrates kernel: [   16.727466] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
May 21 11:37:44 socrates kernel: [   16.761440] cx2388x alsa driver version 0.0.7 loaded
May 21 11:37:44 socrates kernel: [   16.768229] bttv: driver version 0.9.18 loaded
May 21 11:37:44 socrates kernel: [   16.768232] bttv: using 8 buffers with 2080k (520 pages) each for capture
May 21 11:37:44 socrates kernel: [   16.775835] ivtv: Start initialization, version 1.4.1
May 21 11:37:44 socrates kernel: [   16.775865] ivtv: End initialization
May 21 11:37:44 socrates kernel: [   16.818455] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
May 21 11:37:44 socrates kernel: [   16.818464] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
May 21 11:37:44 socrates kernel: [   16.818465]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
May 21 11:37:44 socrates kernel: [   16.818466]  (Note that use of the override may cause unknown side effects.)
May 21 11:37:44 socrates kernel: [   16.818507] amd64_edac: probe of 0000:00:18.2 failed with error -22
May 21 11:37:44 socrates kernel: [   16.818925] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
May 21 11:37:44 socrates kernel: [   16.818927] cx88[0]: TV tuner type 63, Radio tuner type -1
May 21 11:37:44 socrates kernel: [   16.819283] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
May 21 11:37:44 socrates kernel: [   16.819288] HDA Intel 0000:00:0e.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
May 21 11:37:44 socrates kernel: [   16.819290] hda_intel: Disable MSI for Nvidia chipset
May 21 11:37:44 socrates kernel: [   16.876272] Console: switching to colour frame buffer device 80x30
May 21 11:37:44 socrates kernel: [   16.919079] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
May 21 11:37:44 socrates kernel: [   16.919085] nvidia 0000:09:00.0: PCI INT A -> Link[APC6] -> GSI 16 (level, low) -> IRQ 16
May 21 11:37:44 socrates kernel: [   16.919097] vgaarb: device changed decodes: PCI:0000:09:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
May 21 11:37:44 socrates kernel: [   16.919312] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
May 21 11:37:44 socrates kernel: [   16.952204] cx88[0]: i2c init: enabling analog demod on HVR1300/3000/4000 tuner
May 21 11:37:44 socrates kernel: [   16.967776] tuner 1-0043: chip found @ 0x86 (cx88[0])
May 21 11:37:44 socrates kernel: [   16.972719] tda9887 1-0043: creating new instance
May 21 11:37:44 socrates kernel: [   16.972721] tda9887 1-0043: tda988[5/6/7] found
May 21 11:37:44 socrates kernel: [   16.975468] tuner 1-0061: chip found @ 0xc2 (cx88[0])
May 21 11:37:44 socrates kernel: [   17.013343] tveeprom 1-0050: Hauppauge model 69009, rev B2A0, serial# 1241766
May 21 11:37:44 socrates kernel: [   17.013346] tveeprom 1-0050: MAC address is 00:0d:fe:12:f2:a6
May 21 11:37:44 socrates kernel: [   17.013348] tveeprom 1-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
May 21 11:37:44 socrates kernel: [   17.013351] tveeprom 1-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
May 21 11:37:44 socrates kernel: [   17.013353] tveeprom 1-0050: audio processor is CX882 (idx 33)
May 21 11:37:44 socrates kernel: [   17.013355] tveeprom 1-0050: decoder processor is CX882 (idx 25)
May 21 11:37:44 socrates kernel: [   17.013357] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
May 21 11:37:44 socrates kernel: [   17.013359] cx88[0]: hauppauge eeprom: model=69009
May 21 11:37:44 socrates kernel: [   17.021721] tuner-simple 1-0061: creating new instance
May 21 11:37:44 socrates kernel: [   17.021724] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
May 21 11:37:44 socrates kernel: [   17.025693] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:0e.0/0000:02:06.2/input/input4
May 21 11:37:44 socrates kernel: [   17.025766] Creating IR device irrcv0
May 21 11:37:44 socrates kernel: [   17.025768] cx88[0]/2: cx2388x 8802 Driver Manager
May 21 11:37:44 socrates kernel: [   17.026097] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
May 21 11:37:44 socrates kernel: [   17.026101] cx88-mpeg driver manager 0000:02:06.2: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
May 21 11:37:44 socrates kernel: [   17.026108] cx88[0]/2: found at 0000:02:06.2, rev: 5, irq: 16, latency: 32, mmio: 0xfb000000
May 21 11:37:44 socrates kernel: [   17.026113] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
May 21 11:37:44 socrates kernel: [   17.026192] cx8800 0000:02:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
May 21 11:37:44 socrates kernel: [   17.026198] cx88[0]/0: found at 0000:02:06.0, rev: 5, irq: 16, latency: 32, mmio: 0xf9000000
May 21 11:37:44 socrates kernel: [   17.026207] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
May 21 11:37:44 socrates kernel: [   17.032506] wm8775 1-001b: chip found @ 0x36 (cx88[0])
May 21 11:37:44 socrates kernel: [   17.035964] cx88/2: cx2388x dvb driver version 0.0.7 loaded
May 21 11:37:44 socrates kernel: [   17.035967] cx88/2: registering cx8802 driver, type: dvb access: shared
May 21 11:37:44 socrates kernel: [   17.035970] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
May 21 11:37:44 socrates kernel: [   17.035972] cx88[0]/2: cx2388x based DVB/ATSC card
May 21 11:37:44 socrates kernel: [   17.035974] cx8802_alloc_frontends() allocating 2 frontend(s)
May 21 11:37:44 socrates kernel: [   17.038787] cx88[0]/0: registered device video0 [v4l2]
May 21 11:37:44 socrates kernel: [   17.038807] cx88[0]/0: registered device vbi0
May 21 11:37:44 socrates kernel: [   17.038828] cx88[0]/0: registered device radio0
May 21 11:37:44 socrates kernel: [   17.043958] cx88_audio 0000:02:06.1: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
May 21 11:37:44 socrates kernel: [   17.043964] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
May 21 11:37:44 socrates kernel: [   17.043981] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
May 21 11:37:44 socrates kernel: [   17.060056] tuner-simple 1-0061: attaching existing instance
May 21 11:37:44 socrates kernel: [   17.060060] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
May 21 11:37:44 socrates kernel: [   17.062316] DVB: registering new adapter (cx88[0])
May 21 11:37:44 socrates kernel: [   17.062319] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
May 21 11:37:44 socrates kernel: [   17.062654] DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
May 21 11:37:46 socrates kernel: [   19.415482] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:0e.1/input/input5


Help please

---


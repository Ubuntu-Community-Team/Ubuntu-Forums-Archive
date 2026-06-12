---
title: "PixelView PlayTV Xtreme in Ubuntu 7.10"
date: 2008-06-07
forum: Multimedia Software
---

### Post by KhurramF on 2008-06-07
Has anyone got the PixelView PlayTV Xtreme to work in Ubuntu? I get the following from dmesg:

> [  108.138237] CORE cx88[0]: subsystem: 1554:4949, board: UNKNOWN/GENERIC [card=0,autodetected]
[  108.138239] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[  108.202771] cx2388x alsa driver version 0.0.6 loaded
[  108.296270] cx88[0]/0: found at 0000:06:01.0, rev: 5, irq: 17, latency: 64, mmio: 0xfc000000
[  108.425286] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[  108.435730] cx88[0]/0: registered device video0 [v4l2]
[  108.435741] cx88[0]/0: registered device vbi0
[  108.435756] tuner 0-0061: tuner type not set
[  108.435902] ACPI: PCI Interrupt 0000:06:01.1[A] -> GSI 17 (level, low) -> IRQ 17
[  108.435922] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[  108.759482] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[  108.759493] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  109.057120] hda_codec: Unknown model for AD1988, trying auto-probe from BIOS...
[  111.265666] No dock devices found.


xawtv just gives static. I am using 7.10 livecd. 

Btw, Dscaler in XP didnt work with the card either. I have run regspy on XP with the software that came with the card (Honestech TVR 2.5) and can post the output here. It seems that the value of something called MO_GP2_IO changes as I switch between tuner, composite and svideo inputs; the values for MO_GP0_IO, MO_GP1_IO and MO_GP3_IO remain the same (there are some other changes also but these are the ones I get when switching between tuner and composite inputs). I have been googling for this and there was some mention of V4L values for "gpio_set" which sound similar to MO_GPx_IO. Can someone offer some help in this regard?

Thanks.
Khurram.

---

### Post by KhurramF on 2008-06-09
Nobody has used this card with Ubuntu? Very strange.

Khurram.

---

### Post by ispmarin on 2008-10-30
Same board, no luck.

---


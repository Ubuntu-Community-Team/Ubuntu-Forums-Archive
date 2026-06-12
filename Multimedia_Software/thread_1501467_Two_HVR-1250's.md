---
title: "Two HVR-1250's"
date: 2010-06-04
forum: Multimedia Software
---

### Post by Abzstrak on 2010-06-04
I need assistance figuring something out... I'm running 10.04, I have tried using mercurial and the newer v4l-dvb stuff, but that didn't help.

I have added two Hauppauge HVR-1250's to my Mythbackend to catch OTA broadcasts.  I cannot get both of the cards to work together, but each works fine on it's own.  Both cards are exactly identical, both work fine in either PCIe slot that I have them in, but when I put both cards in the system only the first one to be seen is initialized properly.

In order to get the system to see it right, I have to make a /etc/modprobe.d/cx23885.conf 

Now, I think it has something to do with this file.  Somehow I think I need to tell it that the second card is also a type 20.  The line I have in there right now is this:

options cx23885 adapter_nr=0,1 card=20


The first thing that I got to work was this:

options cx23885 card=20

But I have been experimenting and trying to find out some way of telling it to use that card=20 for the second card as well.


My dmesg related output is as follows:

On the first card (the one that is found ok)

[   28.930968] cx23885 driver version 0.0.2 loaded
[   28.931107] cx23885 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.931226] CORE cx23885[0]: subsystem: 0070:2259, board: Hauppauge WinTV-HVR1255 [card=20,insmod option]
[   28.933385] w83627ehf: Found W83627EHG chip at 0x290
[   29.000957] ivtv: Start initialization, version 1.4.1
[   29.078966] tveeprom 0-0050: Hauppauge model 22111, rev E2F5, serial# 7214548
[   29.078968] tveeprom 0-0050: MAC address is 00-0D-FE-6E-15-D4
[   29.078969] tveeprom 0-0050: tuner model is NXP 18271C2 (idx 155, type 54)
[   29.078971] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   29.078973] tveeprom 0-0050: audio processor is CX23888 (idx 40)
[   29.078974] tveeprom 0-0050: decoder processor is CX23888 (idx 34)
[   29.078976] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   29.078977] cx23885[0]: hauppauge eeprom: model=22111
[   29.078979] cx23885_dvb_register() allocating 1 frontend(s)
[   29.078981] cx23885[0]: cx23885 based dvb card



This is from the second card:

[   29.664538] cx23885 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   29.664543] cx23885[1]: Your board isn't known (yet) to the driver.
[   29.664544] cx23885[1]: Try to pick one of the existing card configs via
[   29.664545] cx23885[1]: card=<n> insmod option.  Updating to the latest
[   29.664545] cx23885[1]: version might help as well.
[   29.664547] cx23885[1]: Here is a list of valid choices for the card=<n> insmod option:
[   29.664549] cx23885[1]:    card=0 -> UNKNOWN/GENERIC
[   29.664550] cx23885[1]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   29.664551] cx23885[1]:    card=2 -> Hauppauge WinTV-HVR1800
[   29.664552] cx23885[1]:    card=3 -> Hauppauge WinTV-HVR1250
[   29.664554] cx23885[1]:    card=4 -> DViCO FusionHDTV5 Express
[   29.664555] cx23885[1]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   29.664556] cx23885[1]:    card=6 -> Hauppauge WinTV-HVR1500
[   29.664557] cx23885[1]:    card=7 -> Hauppauge WinTV-HVR1200
[   29.664558] cx23885[1]:    card=8 -> Hauppauge WinTV-HVR1700
[   29.664559] cx23885[1]:    card=9 -> Hauppauge WinTV-HVR1400
[   29.664561] cx23885[1]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   29.664562] cx23885[1]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   29.664563] cx23885[1]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   29.664564] cx23885[1]:    card=13 -> Compro VideoMate E650F
[   29.664566] cx23885[1]:    card=14 -> TurboSight TBS 6920
[   29.664567] cx23885[1]:    card=15 -> TeVii S470
[   29.664568] cx23885[1]:    card=16 -> DVBWorld DVB-S2 2005
[   29.664569] cx23885[1]:    card=17 -> NetUP Dual DVB-S2 CI
[   29.664570] cx23885[1]:    card=18 -> Hauppauge WinTV-HVR1270
[   29.664571] cx23885[1]:    card=19 -> Hauppauge WinTV-HVR1275
[   29.664572] cx23885[1]:    card=20 -> Hauppauge WinTV-HVR1255
[   29.664574] cx23885[1]:    card=21 -> Hauppauge WinTV-HVR1210
[   29.664575] cx23885[1]:    card=22 -> Mygica X8506 DMB-TH
[   29.664576] cx23885[1]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[   29.664577] cx23885[1]:    card=24 -> Hauppauge WinTV-HVR1850
[   29.664578] cx23885[1]:    card=25 -> Compro VideoMate E800
[   29.664657] CORE cx23885[1]: subsystem: 0070:2259, board: UNKNOWN/GENERIC [card=0,autodetected]
[   29.792147] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   29.792154] cx23885[1]/0: found at 0000:03:00.0, rev: 4, irq: 19, latency: 0, mmio: 0xfe800000
[   29.792160] cx23885 0000:03:00.0: setting latency timer to 64
[   29.792163] IRQ 19/cx23885[1]: IRQF_DISABLED is not guaranteed on shared IRQs



Backend System specs
780G chipset mobo, Athlon X4 620, 4GB RAM, two PVR-150's and one PVR 500.  Six 500GB drives in software RAID5.

---

### Post by Abzstrak on 2010-06-07
anyone have any ideas?

---

### Post by Abzstrak on 2010-06-09
This is fixed, any discussion will be only posted here : [http://www.mythtvtalk.com/forum/hardware/13295-two-hvr-1250s.html#post52379](http://www.mythtvtalk.com/forum/hardware/13295-two-hvr-1250s.html#post52379)

---


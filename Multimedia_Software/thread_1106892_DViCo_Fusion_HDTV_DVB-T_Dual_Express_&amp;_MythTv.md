---
title: "DViCo Fusion HDTV DVB-T Dual Express &amp; MythTv"
date: 2009-03-26
forum: Multimedia Software
---

### Post by XPomJon on 2009-03-26
I'm trying to get Mythtv to work with a DViCo FusionHDTV DVB-T Dual Express card but I've fallen at the second hurdle. The problem seems to be that the card isn't autoloaded.
Output of dmesg:-
```
 10.764348] Linux video capture interface: v2.00
[   10.798096] gspca: main v2.5.0 registered
[   10.827321] gspca: probing 046d:08d9
[   10.945141] cx23885 driver version 0.0.1 loaded
[   10.945184] cx23885 0000:01:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[   10.945187] cx23885[0]: Board has no valid PCIe Subsystem ID and can't
[   10.945188] cx23885[0]: be autodetected. Pass card=<n> insmod option
[   10.945188] cx23885[0]: to workaround that. Redirect complaints to the
[   10.945189] cx23885[0]: vendor of the TV card.  Best regards,
[   10.945190] cx23885[0]:         -- tux
[   10.945191] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   10.945192] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   10.945193] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   10.945195] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   10.945196] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   10.945197] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   10.945198] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   10.945199] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   10.945200] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   10.945201] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   10.945203] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   10.945204] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   10.945205] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   10.945206] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   10.945207] cx23885[0]:    card=13 -> Compro VideoMate E650F
[   10.945208] cx23885[0]:    card=14 -> TurboSight TBS 6920
[   10.945210] cx23885[0]:    card=15 -> TeVii S470
[   10.945211] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[   10.945212] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[   10.945268] CORE cx23885[0]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   11.071449] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   11.071456] cx23885[0]/0: found at 0000:01:00.0, rev: 2, irq: 28, latency: 0, mmio: 0xf7e00000
[   11.071462] cx23885 0000:01:00.0: setting latency timer to 64

```

Can anyone tell me how I use card = <n> insmod option. I've looked at the insmod man page and googled but to no avail.

Thanks...

---

### Post by bspicoli13 on 2011-01-07
I have a DviCo fusionhdtv 7 dual express that uses the same driver and is also not *auto*-*detected*.  I solved my problem by issuing these commands:

modprobe -r cx23885
modprobe cx23885 card=10
service mythtv-backend restart

you would need to change 10 to 11.

You can make this change permanent in Ubuntu 10.10 by creating a file.

sudo su
cd /etc/modprobe.d/
echo "options cx23885 card=11" > cx23885.conf

with this file in place your card will be setup properly on boot

---


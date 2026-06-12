---
title: "WinTV HVR 1500 Express Card"
date: 2008-08-06
forum: Mythbuntu
---

### Post by kshsj777 on 2008-08-06
Does anyone use this card?  I'd like to know if it will display closed caption with myth tv or another linux tv program.  

I wrote to hauppauge support and they said the card supports CC but then recommended I run it under media center or beyond tv, neither of which run on linux as far as I know. I even put that I was using ubuntu 8.04 and planned to use myth tv but... *shrugs shoulders*

---

### Post by kshsj777 on 2008-08-08
So no one uses this card?  I don't have a pci slot so I unless I want to use a usb this is the only express card supported so far.

---

### Post by bazmati on 2008-11-12
Hi, I,m about to purchase a laptop (SL500 Thinkpad probably) and i do want TV on it and so after reading your post i found 

[http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html)

Stating that 

Linux support for the WinTV-HVR-1200, WinTV-HVR-1500 and WinTV-HVR-1500Q 
is under way.

Linux support for the WinTV-HVR-1600 is in the upcoming kernel 2.6.26 release.

Also, there is WinTV-HVR-1600 Linux support for both the analog TV tuner and the digital TV tuner available at LinuxTV.ORG in the "cx18" section.


----------
THERE IS HOPE COMING SOON

---

### Post by markackerman8@gmail.com on 2009-12-10
WinTV-HVR-1500 is driving me crazy .... any help would be greatly appreciated so I dont go back to windows ARGHHHH
nothing I do can seem to get my tuner card to show anything

here's my dmesg

cx23885 driver version 0.0.2 loaded
[    8.602182] cx23885 0000:04:00.0: enabling device (0000 -> 0002)
[    8.602191] cx23885 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.602315] CORE cx23885[0]: subsystem: 0070:7797, board: Hauppauge WinTV-HVR1500Q [card=5,autodetected]
[    8.732278] tveeprom 0-0050: Hauppauge model 77041, rev E2F0, serial# 3746385
[    8.732282] tveeprom 0-0050: MAC address is 00-0D-FE-39-2A-51
[    8.732285] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[    8.732288] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[    8.732291] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[    8.732293] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[    8.732295] tveeprom 0-0050: has no radio
[    8.732297] cx23885[0]: hauppauge eeprom: model=77041
[    8.732300] cx23885_dvb_register() allocating 1 frontend(s)
[    8.733646] cx23885[0]: cx23885 based dvb card
[    8.767783] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
......
......
[    8.897116] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[    8.925521] xc5000 1-0061: creating new instance
[    8.926237] xc5000: Successfully identified at address 0x61
[    8.926239] xc5000: Firmware has not been loaded previously
[    8.926243] DVB: registering new adapter (cx23885[0])
[    8.926247] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[    8.926528] cx23885_dev_checkrevision() Hardware revision = 0xb0
[    8.926539] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf6000000
[    8.926550] cx23885 0000:04:00.0: setting latency timer to 64
[    8.926556] IRQ 17/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.244905]   alloc irq_desc for 22 on node 0
[    9.244908]   alloc kstat_irqs on node 0
[    9.244917] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.244977] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.383292] phy0: Selected rate control algorithm 'iwl-agn-rs'



HELPPPP

---

### Post by oliver.greg@gmail.com on 2009-12-25
I just got one of these cards (1500Q), and mine is working fine with MythTV - cx23885 setup for dvb...

What software are you using?  I am on a vanilla Karmic install, but using the 2.6.32-rc8 kernel from the ubuntu kernel ppa rather than the karmic supplied version..  That may help you out as well.

---

### Post by markackerman8@gmail.com on 2010-03-23
I am back to consider trying yhis again as I am coming back to ubuntu to give mythtv a fair try.  So in answer to to the question, I am using Ubuntu 9.10.  

I would REALLY appreciate any optimism for any possible analog ntsc cable support in linux!!!

---

### Post by iponeverything on 2010-03-23
I have done some google'ing around around and I would not be optimistic about the WinTV HVR 1500 working with mythtv.

---

### Post by markackerman8@gmail.com on 2010-03-23
I even sent an email to Hauppauge for their promised support.  They have been saying analog support in linux is in progress for 1 1/2years!

---

### Post by iponeverything on 2010-03-24
> **markackerman8@gmail.com said:**
> I even sent an email to Hauppauge for their promised support.  They have been saying analog support in linux is in progress for 1 1/2years!

That is pretty good sign that perhaps you should buy a different card.  Some of the Hauppauge cards are quite good in mythtv.

---

### Post by markackerman8@gmail.com on 2010-03-26
Hauppauge's response to me was that they don't promise anything for Linux. arghhhh!

---

### Post by markackerman8@gmail.com on 2010-04-19
Just as an update, I took the advice and tried a few different cards, and here is my experience, and I hope it helps someone.  Believe me when I say I have tried just about everything with these cards to get them to work with analog cable and mythtv.  All references of functionality here are related to NTSC analog cable.

HVR-950Q - works with TVtime, not with MythTV, needs a few tricks to get it from reloading its module all the time.

HVR-850 - no luck with MythTV

WinTV-PVR-USB2 - works ONLY with MythTV (and reportedly with tv-viewer as well)

HVR-1500Q - only working with antennae ATSC for me

---


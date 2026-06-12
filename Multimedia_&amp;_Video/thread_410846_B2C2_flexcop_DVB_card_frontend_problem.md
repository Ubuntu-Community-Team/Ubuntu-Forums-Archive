---
title: "B2C2 flexcop DVB card frontend problem"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by Suolx on 2007-04-16
LSPCI:
05:01.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)

DMESG:
   68.456812] b2c2-flexcop: found the lgdt3303 at i2c address: 0x59
[   68.456815] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   68.456832] b2c2-flexcop: initialization of 'Air2PC/AirStar 2 ATSC 3rd generation (HD5000)' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

LSMOD:
dvb_core               93552  3 lgdt330x,stv0299,b2c2_flexcop
dvb_pll                17220  2 lgh06xf,b2c2_flexcop

Problem is that I don't want that freaking ATSC frontend but I want stv0297 dvb-c frontend.
I had it working like a charm with 2.6.21-rc6 kernel and then tested other kernels and now it wants to install
ATSC frontend as default. How can I get it to load STV0297 dvb-c frontend instead LGDT330X ATSC?

---


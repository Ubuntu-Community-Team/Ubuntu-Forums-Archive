---
title: "Nova-T 500 in 10.1 - problems using"
date: 2011-02-26
forum: Multimedia Software
---

### Post by dbrb2 on 2011-02-26
Hello,

I have just installed Ubuntu 10.1 x64 on my desktop, haviing been running Windows for a bit.

My desktop has two tuner cards: 

1 x Nova-T 500 hauppage card (dual tuner)
and one TBS 6920 DVB-S2 card

I have built the drivers for the TBS card as per the instructions here:
[http://www.tbsdtv.com/english/Download.html](http://www.tbsdtv.com/english/Download.html)

But can't get the Hauppage card to work at all. 
lsusb gives: 
Bus 002 Device 002: ID 2040:9951 Hauppauge

dmesg shows: 

[   14.399580] cx25840 4-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   14.407110] cx23885_dvb_register() allocating 1 frontend(s)
[   14.407115] cx23885[0]: cx23885 based dvb card
[   14.410543] DVB: registering new adapter (cx23885[0])
[   14.410548] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[   14.437672] TurboSight TBS 6920 MAC= 00:22:AB:E0:0A:19
[   14.437677] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   14.437684] cx23885[0]/0: found at 0000:03:00.0, rev: 2, irq: 16, latency: 0, mmio: 0xfa000000
[   14.437690] cx23885 0000:03:00.0: setting latency timer to 64


But if I try a scan I get: 

@ben-desktop:/usr/share/dvb/dvb-t$ w_scan -c GB
w_scan version 20100316 (compiled for DVB API 5.1)
using settings for UNITED KINGDOM
DVB aerial
DVB-T GB
frontend_type DVB-T, channellist 6
output format vdr-1.6
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> DVB-S "Conexant CX24116/CX24118": specified was DVB-T -> SEARCH NEXT ONE.
main:2930: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

Any pointers?

---

### Post by dbrb2 on 2011-02-26
Oh, and btw - the DVBS card is working fine. Also this should be tagged [Ubuntu] not [kubuntu] - slip of the mouse on my part

---


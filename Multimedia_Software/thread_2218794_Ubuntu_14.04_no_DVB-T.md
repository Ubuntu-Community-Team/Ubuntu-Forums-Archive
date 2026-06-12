---
title: "Ubuntu 14.04 no DVB-T"
date: 2014-04-22
forum: Multimedia Software
---

### Post by malley-vinom on 2014-04-22
I've tried upgrading from 13.10 & a fresh install of Ubuntu 14.04, but both have the same problem, I've got no dvb-t.

TV card I have is a Hauppauge nova-t 500 dual tuner, dvb-t works fine under 13.10 using vlc with my channel list, but get nothing with 14.04, also tried using tvtime, but doesn't find the video source, only my webcam.

The Tuner seems to be loading ok with lspci & lsusb.
04:07.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) 
04:07.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
04:07.2 USB controller: VIA Technologies, Inc. USB 2.0 (rev 65)
 
Bus 004 Device 002: ID 2040:9950 Hauppauge WinTV Nova-T-500

Any ideas? I'll have to go back to 13.10 if I can't solve this in the next couple of days.

TIA
malleybo

---

### Post by malley-vinom on 2014-04-23
I've tried upgrading from 13.10 & a fresh install of Ubuntu 14.04, but both have the same problem, I've got no dvb-t.

TV card I have is a Hauppauge nova-t 500 dual tuner, dvb-t works fine  under 13.10 using vlc with my channel list, but get nothing with 14.04,  also tried using tvtime, but doesn't find the video source, only my  webcam.

The Tuner seems to be loading ok with lspci & lsusb.
04:07.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) 
04:07.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
04:07.2 USB controller: VIA Technologies, Inc. USB 2.0 (rev 65)
 
Bus 004 Device 002: ID 2040:9950 Hauppauge WinTV Nova-T-500

Any ideas? I'll have to go back to 13.10 if I can't solve this in the next couple of days.

TIA
malleybo

---

### Post by mörgæs on 2014-04-23
Please open only one thread per problem.
Merged.

---

### Post by caish5-hotmail on 2014-04-23
I'm having the same problem in 14.04 using a USB DVB-T receiver that used to work fine in 13.10 and previous versions.

---

### Post by malley-vinom on 2014-04-24
> **caish5-hotmail said:**
> I'm having the same problem in 14.04 using a USB DVB-T receiver that used to work fine in 13.10 and previous versions.


Fixed it, I was using my channels.conf from my scanned channels in 13.10, try rescanning your channels,

scan /usr/share/dvb/dvb-t/uk-CrystalPalace >./channels.conf

Replace uk-CrystalPalace with your local transmitter, see if that works?

malleybo

---


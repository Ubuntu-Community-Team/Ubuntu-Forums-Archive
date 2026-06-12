---
title: "scanning for channels for a channels.conf file"
date: 2008-12-20
forum: Multimedia Software
---

### Post by fishbulb1022 on 2008-12-20
Hi, I'm trying to use an Ati hdtv wonder 600 usb tuner. It is supported, according to the linuxtv wiki. My computer finds it in the dev folder. I've been trying to scan for channels using san and w_scan. Neither finds any channels. when I use w_scan, this is what I get. 

w_scan version 20081106
Info: using DVB adapter auto detection.
   Found ATSC frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend LG Electronics LGDT3303 VSB/QAM Frontend supports
FE_CAN_8VSB
FE_CAN_QAM_64
FE_CAN_QAM_256
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 
63000: 
69000: 
79000: 
85000: 
177000: 
183000: 
189000: 
195000: 
201000: 
207000: 
213000: 
473000: 
479000: 
485000: 
491000: 
497000: 
503000: 
509000: 
515000: 
521000: 
527000: 
533000: 
539000: 
545000: 
551000: 
557000: 
563000: 
569000: 
575000: 
581000: 
587000: 
593000: 
599000: 
605000: 
611000: 
617000: 
623000: 
629000: 
635000: 
641000: 
647000: 
653000: 
659000: 
665000: 
671000: 
677000: 
683000: 
689000: 
695000: 
701000: 
707000: 
713000: 
719000: 
725000: 
731000: 
737000: 
743000: 
749000: 
755000: 
761000: 
767000: 
773000: 
779000: 
785000: 
791000: 
797000: 
803000: 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.

does anyone have any advice?

---

### Post by avacado on 2010-01-14
fishbulb 1022, I get exactly the same

a@gollum:~$ w_scan -ft -c AU -x >> channel.conf
w_scan version 20090808 (compiled for DVB API 5.0)
using settings for AUSTRALIA
DVB aerial
DVB-T AU
frontend_type DVB-T, channellist 3
output format initial tuning data
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> DVB-T "Zarlink ZL10353 DVB-T": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.0
frontend Zarlink ZL10353 DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00) 
177625: (time: 00:03) 
184500: (time: 00:05) 

## and so on many times over

809625: (time: 04:40) 
816500: (time: 04:43) 
816625: (time: 04:45) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

I have tried the au-ALL.txt file which is supposed to be a channels.conf file for all the possible combinations in australia, but I can;t get that to work in klear or metv and starting to think it is too hard.

---

### Post by TopEnder on 2010-01-17
G'Day avacado and fishbulb1022,  There is a newer version of me-tv, ver: 1.1.5 it may solve your problem.  When I updated to me-tv ver: 1.1.4, I had to rescan all the channels from with in me-tv I have to scan  both Darwin & Adelaide to get all available channels in my area.  
When I originally set-up my dvb-t I had the same problems as indicated in fishbulb1022 post and I think I eventually got round it by using dvbscan how I did it was to check the forum out on dvbscan and follow the advice (to old to remember what I did last week let alone a year or two ago).  TopEnder

---


---
title: "Msi Mega Sky 580 (ID=0db0:5581)"
date: 2008-09-04
forum: Multimedia Software
---

### Post by kaefert66014235 on 2008-09-04
Okey, so I'm giving it another try to get my DVB-T stick to work in Ubuntu 8.04

The monolog of my first (only partly successful) try can be found here:
[http://ubuntuforums.org/showthread.php?t=829141](http://ubuntuforums.org/showthread.php?t=829141)

So the begining is the same, Install Ubuntu and be happy that the device gets detected as DVB-T devive. Kaffeine names it "Zarlink ZL10353 DVB-T".

Then, when trying to scan for channels, or trying a prepared channels.conf for my area -->
```
RF1:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1010:1011:10101
ORF2W:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1020:1021:10102
ORF2N:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1020:1021:10122
ATV+:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1040:1041:10120
PULS 4:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1050:1051:10123
3SAT:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1055:1056:11102
ORF Sport Plus:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1060:1061:11103
```

you come down to earth again. Unlike last time I tried this, not a single channel works.

Nobody can tell me that the signal is too weak, since first I'm living in the middle of the city, and second in windows with the exact same hardware and with everything on the exact same place all 7 Austrian channels are recieveable.

Okey, so next thing I tried was w_scan, that I knew from last time trying to get this to work ([http://wirbel.htpc-forum.de/w_scan](http://wirbel.htpc-forum.de/w_scan))

```
kaefert@Blechkiste:~/Daten/w_scan-20080815$ ./w_scan
w_scan version 20080815
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend Zarlink ZL10353 DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
177500: 
184500: 
191500: 
198500: 
205500: 
212500: 
219500: 
226500: 
474000: 
482000: 
490000: 
498000: 
506000: 
514000: 
522000: 
530000: 
538000: 
546000: 
554000: 
562000: 
570000: 
578000: 
586000: 
594000: 
602000: 
610000: 
618000: 
626000: 
634000: 
642000: 
650000: 
658000: 
666000: 
674000: 
682000: 
690000: 
698000: 
706000: 
714000: 
722000: 
730000: 
738000: 
746000: 
754000: 
762000: 
770000: 
778000: 
786000: 
794000: 
802000: 
810000: 
818000: 
826000: 
834000: 
842000: 
850000: 
858000: 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.
kaefert@Blechkiste:~/Daten/w_scan-20080815$ 

```

Okey, so lets continue my search.
[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#MSI_Mega_Sky_55801_DVB-T_USB2.0](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#MSI_Mega_Sky_55801_DVB-T_USB2.0) tells me, that this device is working out of the box.. or at least some device named very similar. as if...

there [http://ubuntuforums.org/showthread.php?t=319727](http://ubuntuforums.org/showthread.php?t=319727) where some people talking about this stick, but since this discussion is over a year old, i don't think that the info to have to manually install drivers is still valid for Ubuntu 8.04

there [http://forums.gentoo.org/viewtopic-t-477817.html](http://forums.gentoo.org/viewtopic-t-477817.html) someone reported he got the stick with the ID 0db0:5581 working..

I would try the driver the both discussions above reference, but the link [http://linuxtv.org/hg/~mkrufky/megasky](http://linuxtv.org/hg/~mkrufky/megasky) isn't valid anymore.

If anyone is reading this, please tell me what else i could do to get this thing working

---

### Post by potnoodles on 2008-10-27
Ive got it working in 8.04 64 and 32 bit versions.(using Kaffeine)
Found your post while looking up my previous posts (install instructions) in order to try this out on the PS3.

My probs with 8.04 (sorted)
[http://ubuntuforums.org/showthread.php?t=768751&highlight=megasky](http://ubuntuforums.org/showthread.php?t=768751&highlight=megasky)

Original Gutsy install(solved)
[http://ubuntuforums.org/showthread.php?t=587130&highlight=megasky](http://ubuntuforums.org/showthread.php?t=587130&highlight=megasky)

I have to re-copy the firmware(edit: to the relevant firmware folder) manually after each  new kernal update

good luck

---


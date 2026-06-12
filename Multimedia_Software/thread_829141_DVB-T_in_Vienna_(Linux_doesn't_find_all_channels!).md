---
title: "DVB-T in Vienna (Linux doesn't find all channels!)"
date: 2008-06-14
forum: Multimedia Software
---

### Post by kaefert66014235 on 2008-06-14
Hi there! I've got a DVB-T Stick ("MSI MODEL MS-5580 MEGA SKY") that got detected by Ubuntu 8.04 without me doing anything. The only problem is, that only 3 of 7 channels get found, and even when manually configuring them into the Channels.conf (see below) i get no audio or video. That wouldn't be that strange (I mean maybe they arn't sending strong enought) but the 4 channels that don't work in Linux work perfectly with the microsoft windows software that was supplied by MSI when I bought the DVB-T stick.

I've found some Channels.conf on the web that is ment for Vienna, but that doesn't work for me (somehow this different channel.conf syntax doesn't work for the software I tried (ME TV & Totem))
[http://www.vdr-wiki.de/wiki/index.php/Channels.conf_DVBT-AT-Wien](http://www.vdr-wiki.de/wiki/index.php/Channels.conf_DVBT-AT-Wien)

Here's my Channels.conf that works for the channels 3Sat, Puls4 & Orf Sport Plus:
```
ORF1:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1010:1011:10101
ORF2W:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1020:1021:10102
ORF2N:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1020:1021:10122
ATV+:498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:1040:1041:10120
PULS 4:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1050:1051:10123
3SAT:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1055:1056:11102
ORF Sport Plus:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1060:1061:11103
```

The by MSI supplied MS Windows software prints the following table as channel settings:
```
Channel         Frequenzy Video-ID Audio-ID
ORF1            498000    1010     1011,1013
ORF2W           498000    1020     1021,1023
ORF2N           498000    1020     1021,1023
ATV             498000    1040     1041
Puls TV Austria 578000    1050     1051
3SAT            578000    1055     1056,1057
ORF Sport Plus  578000    1060     1061
```

If you look at my channels.conf (first code-box) i took these and added the service-ids from the channels.conf @ [http://www.vdr-wiki.de/wiki/index.php/Channels.conf_DVBT-AT-Wien](http://www.vdr-wiki.de/wiki/index.php/Channels.conf_DVBT-AT-Wien)
This works perfectly for the 3 channels puls4, 3sat & orf sport plus, but these get detected anyway. the other 4 channels keep dark, althought they work with the same antenna under windows.

I don't know if it helps but here i added the output of w_scan ([http://www.vdr-wiki.de/wiki/index.php/W_scan):](http://www.vdr-wiki.de/wiki/index.php/W_scan):)
```
kaefert@Mobulux:~/Desktop/Fernsehen/w_scan-20080105$ ./w_scan
w_scan version 20080105
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
578000: signal ok (I999B8C999D999M999T999G999Y999)
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
tune to: :578000:I999B8C999D999M999T999G999Y999:T:27500:
     PULS 4(sevenonemedia)
     3SAT(ORF)
     ORF Sport Plus(ORF)
Network Name 'ORS DVB-T W2'
copying transponder info (578000)
dumping lists (3 services)
PULS 4:578000:I999B8C34D34M16T8G8Y0:T:27500:1050:1051=ger:1052:0:10123:8232:110:0
3SAT:578000:I999B8C34D34M16T8G8Y0:T:27500:1055:1056=ger,1057=eng:1058:0:11102:8232:110:0
ORF Sport Plus:578000:I999B8C34D34M16T8G8Y0:T:27500:1060:1061=ger:0:0:11103:8232:110:0
Done.
```

====================================================================================================================================0


I also tried to take the frequenzy list of the ors ([http://blog.ors.at/stories/15461/](http://blog.ors.at/stories/15461/)) and wrote an input file for the in ubuntu included tool "scan":
```
# All official DVB-T Transponders run by the ORS (for Austria)
# updated: 06/2008 (source of transponderlist: http://blog.ors.at/stories/15461/)
#T  freq    bw   fec_hi fec_lo mod   transmission-mode guard-interval hierarchy

T 474000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K21, ??
T 482000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K22, ??
T 490000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K23, Innsbruck
T 498000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K24, Bregenz
T 506000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K25, ??
T 514000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K26, ??
T 522000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K27, ??
T 530000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K28, ??
T 538000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K29, ??
T 546000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K30, ??
T 554000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K31, ??
T 562000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K32, Salzburg (w/ overspill to Germany) && Linz, Amstetten (NÖ)
T 570000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K33, ??
T 578000000 8MHz 3/4    NONE   QAM16 8k                1/8            NONE #K34, (bei MUXB in Wien Kanal 34 = 1/8)
T 586000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K35, ??
T 594000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K36, ??
T 602000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K37, ??
T 610000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K38, ??
T 618000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K39, ??
T 626000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K40, ??
T 634000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K41, ??
T 642000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K42, ??
T 650000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K43, ??
T 658000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K44, ??
T 666000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K45, ??
T 674000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K46, ??
T 682000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K47, ??
T 690000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K48, ??
T 698000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K49, ??
T 706000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K50, ??
T 714000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K51, ??
T 722000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K52, ??
T 730000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K53, ??
T 738000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K54, ??
T 746000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K55, ??
T 754000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K56, Eisenstadt
T 762000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K57, ??
T 770000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K58, ??
T 778000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K59, ??
T 786000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K60, ??
T 794000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K61, Wien
T 802000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K62, Graz && Graz, Klagenfurt, Viktring (Ktn.)
T 810000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K63, ??
T 818000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K64, ??
T 826000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K65, ??
T 834000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K66, ??
T 842000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K67, ??
T 850000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K68, St.Pölten
T 858000000 8MHz 3/4    NONE   QAM16 8k                1/4            NONE #K69, ??
```

Scan does the following when fed with the list above:
```
kaefert@Mobulux:/usr/share/doc/dvb-utils/examples/scan/dvb-t$ scan at-ALL
scanning at-ALL
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 474000000 0 3 9 1 1 3 0
initial transponder 482000000 0 3 9 1 1 3 0
initial transponder 490000000 0 3 9 1 1 3 0
initial transponder 498000000 0 3 9 1 1 3 0
initial transponder 506000000 0 3 9 1 1 3 0
initial transponder 514000000 0 3 9 1 1 3 0
initial transponder 522000000 0 3 9 1 1 3 0
initial transponder 530000000 0 3 9 1 1 3 0
initial transponder 538000000 0 3 9 1 1 3 0
initial transponder 546000000 0 3 9 1 1 3 0
initial transponder 554000000 0 3 9 1 1 3 0
initial transponder 562000000 0 3 9 1 1 3 0
initial transponder 570000000 0 3 9 1 1 3 0
initial transponder 578000000 0 3 9 1 1 2 0
initial transponder 586000000 0 3 9 1 1 3 0
initial transponder 594000000 0 3 9 1 1 3 0
initial transponder 602000000 0 3 9 1 1 3 0
initial transponder 610000000 0 3 9 1 1 3 0
initial transponder 618000000 0 3 9 1 1 3 0
initial transponder 626000000 0 3 9 1 1 3 0
initial transponder 634000000 0 3 9 1 1 3 0
initial transponder 642000000 0 3 9 1 1 3 0
initial transponder 650000000 0 3 9 1 1 3 0
initial transponder 658000000 0 3 9 1 1 3 0
initial transponder 666000000 0 3 9 1 1 3 0
initial transponder 674000000 0 3 9 1 1 3 0
initial transponder 682000000 0 3 9 1 1 3 0
initial transponder 690000000 0 3 9 1 1 3 0
initial transponder 698000000 0 3 9 1 1 3 0
initial transponder 706000000 0 3 9 1 1 3 0
initial transponder 714000000 0 3 9 1 1 3 0
initial transponder 722000000 0 3 9 1 1 3 0
initial transponder 730000000 0 3 9 1 1 3 0
initial transponder 738000000 0 3 9 1 1 3 0
initial transponder 746000000 0 3 9 1 1 3 0
initial transponder 754000000 0 3 9 1 1 3 0
initial transponder 762000000 0 3 9 1 1 3 0
initial transponder 770000000 0 3 9 1 1 3 0
initial transponder 778000000 0 3 9 1 1 3 0
initial transponder 786000000 0 3 9 1 1 3 0
initial transponder 794000000 0 3 9 1 1 3 0
initial transponder 802000000 0 3 9 1 1 3 0
initial transponder 810000000 0 3 9 1 1 3 0
initial transponder 818000000 0 3 9 1 1 3 0
initial transponder 826000000 0 3 9 1 1 3 0
initial transponder 834000000 0 3 9 1 1 3 0
initial transponder 842000000 0 3 9 1 1 3 0
initial transponder 850000000 0 3 9 1 1 3 0
initial transponder 858000000 0 3 9 1 1 3 0
>>> tune to: 474000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 474000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 482000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 482000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 490000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 498000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 530000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 530000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 538000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 538000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 546000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 546000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 554000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 554000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0000 0x278b: pmt_pid 0x0096 sevenonemedia -- PULS 4 (running)
0x0000 0x2b5e: pmt_pid 0x0097 ORF -- 3SAT (running)
0x0000 0x2b5f: pmt_pid 0x0098 ORF -- ORF Sport Plus (running)
Network Name 'ORS DVB-T W2'
>>> tune to: 586000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 586000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 594000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 594000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 602000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 610000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 610000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 618000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 618000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 634000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 634000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 642000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 642000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 658000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 666000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 666000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 682000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 682000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 690000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 690000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 706000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 706000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 714000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 714000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 722000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 722000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 730000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 730000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 738000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 738000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 746000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 746000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 754000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 762000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 762000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 770000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 770000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 778000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 778000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 786000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 786000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 794000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 794000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 802000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
ERROR: interrupted by SIGINT, dumping partial result...
dumping lists (3 services)
PULS 4:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1050:1051:10123
3SAT:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1055:1056:11102
ORF Sport Plus:578000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:1060:1061:11103
Done.
kaefert@Mobulux:/usr/share/doc/dvb-utils/examples/scan/dvb-t$ 
```

If anyone got any idea what the problem could be, that i cant find 4 of the 7 channels I see in the windows software (is there maybe some ciphering or something like that?) please tell me. Also please tell me if you know if the service-ids from [http://www.vdr-wiki.de/wiki/index.php/Channels.conf_DVBT-AT-Wien](http://www.vdr-wiki.de/wiki/index.php/Channels.conf_DVBT-AT-Wien) are right. I considered they where, since all the frequencies and the audio & video-ids are the same as the windows software that shows the channels correctly.

Thanks for your help!

---

### Post by Trollslayer on 2008-06-14
Is it encrypted channels you have a problem with?

---

### Post by kaefert66014235 on 2008-06-14
well I am not sure, but the windows software didn't need anything, and even if the channels where encrypted, shouldn't "w_scan" and/or "scan" at least find the channels? they should be (as you can see in the posted configs) @ frequence 498mhz, but neither "w_scan" nor "scan" finds anything at that frequence..

---

### Post by ronzo on 2008-11-22
Similar problem here...

I am using a pinnacle DVB-T stick (72e). On my laptop (OS: Ubuntu Intrepid), all channels were found and viewing them went smoothly using me-tv.

w_scan finds 7 channels (ORF1, ORF2 Wien, ORF2 Niederösterreich and ATV on 498 MHz; Puls 4, 3Sat and ORF Sport Plus on 578 Mhz).

On another PC (Ubuntu Intrepid) using VDR, the channels on 578 Mhz cannot be viewed.

w_scan finds them but if I try

```
w_scan -fc -x > initial_tuning_data.txt
dvbscan -o vdr -p -e 6 initial_tuning_data.txt > channels.conf
```

dvbscan says "tuning failed" when trying to tune to the 578 Mhz channels.

If i let w_scan write the vdr channels.conf, it works but vdr does not display the 578 Mhz channels (once it worked for a very short time but it stopped working some minutes later).

Could you find a solution for your problems?

---

### Post by kaefert66014235 on 2008-11-22
> **ronzo said:**
> Similar problem here...

I am using a pinnacle DVB-T stick (72e). On my laptop (OS: Ubuntu Intrepid), all channels were found and viewing them went smoothly using me-tv.

w_scan finds 7 channels (ORF1, ORF2 Wien, ORF2 Niederösterreich and ATV on 498 MHz; Puls 4, 3Sat and ORF Sport Plus on 578 Mhz).

On another PC (Ubuntu Intrepid) using VDR, the channels on 578 Mhz cannot be viewed.

w_scan finds them but if I try

```
w_scan -fc -x > initial_tuning_data.txt
dvbscan -o vdr -p -e 6 initial_tuning_data.txt > channels.conf
```

dvbscan says "tuning failed" when trying to tune to the 578 Mhz channels.

If i let w_scan write the vdr channels.conf, it works but vdr does not display the 578 Mhz channels (once it worked for a very short time but it stopped working some minutes later).

Could you find a solution for your problems?

hi there!
well my solution was buying another dvbt-stick for linux and using that one only with windows...

sorry to can't tell you better news. but if you find something, please let me know!

---

### Post by ronzo on 2008-11-22
Do you have a DVB-T stick in use that works without problems under VDR? If yes, please let me know which one it is... (Do all seven channels MUX A and MUX B work?)

---

### Post by kaefert66014235 on 2008-11-22
yes, that one: [http://geizhals.at/a327244.html](http://geizhals.at/a327244.html) (MSI DigiVox mini II V3)
but the remote control doesnt work. i mean i didnt put any work into it getting it to work, but it doesnt work out of the box

---

### Post by ronzo on 2008-11-22
Thank you! Perfect!

I don't need the RC anyway...

---

### Post by ronzo on 2008-11-24
The stick you recommended is not detected automatically under Ubuntu Itrepid (8.10)... 

```
[  257.916106] usb 3-3: new high speed USB device using ehci_hcd and address 5
[  258.054392] usb 3-3: configuration #1 chosen from 1 choice
[  258.063304] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 16 -> 8
[  258.065584] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1a.7/usb3/3-3/3-3:1.1/input/input14
[  258.128257] input,hidraw2: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1a.7-3

```

---

### Post by kaefert66014235 on 2008-11-24
hmm?! thats strange.. can you tell me the id of your device? is it 15a4:9016? find it with the command "lsusb"

edit: ups.. sorry.. just found out that it doesn't work out of box.. i already forgot that i needed to install a driver for it --> 

BEFORE FOLLOWING THE INSTRUCTIONS BELOW, CHECK THAT YOUR DEVICE GOT THE ID "15a4:9016"

1.) download [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw) and move/copy the file to "/lib/firmware/"
2.) download [http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz](http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz)
3.) extract, change into extracted dir
4.) run "make all"
5.) run "sudo make install"
6.) reboot
7.) have fun watching tv

---

### Post by ronzo on 2008-11-30
Thank you! The stick is working... but I still don't get the MuxB-channels (Puls 4, 3Sat, ORF Sport Plus). (same problem with the pinnacle stick and another hauppauge stick... how can I determine if my signal for those channels is to weak? Which antenna could I buy to strenghten the signal?)

I do not get a 'HAS_LOCK' on the MuxB channels. However, the 'femon-plugin' on VDR shows a signal that never leaves the green area. What's wrong here? I assume that the signal should be perfect (Vienna, 7th district) but I am living in an old building with very thick walls.

---

### Post by kaefert66014235 on 2008-11-30
Hmmm.. strange.. for me the same stick with the same drivers works for all the seven channels that there are over dvb-t in austria. im living in the 3rd district of vienna.

can you try the stick on a pc with ms windows?

---

### Post by ronzo on 2008-11-30
The MSI stick won't work at all under WinXP, the Hauppauge works without any problems (all 7 channels recognized - perfect signal). (I haven't tested the Pinnacle stick under Windows yet.)

Do you use Ubuntu Hardy or Intrepid? Maybe I'll try the stick with a Fedora and a Knoppix LiveCD and see if I can determine different behaviour.

---

### Post by kaefert66014235 on 2008-12-01
I'm still using 8.04 hardy, havn't got time yet for updating to 8.10

---

### Post by ronzo on 2008-12-01
I'll check it out on my fileserver which still runs Hardy. We'll see...

---


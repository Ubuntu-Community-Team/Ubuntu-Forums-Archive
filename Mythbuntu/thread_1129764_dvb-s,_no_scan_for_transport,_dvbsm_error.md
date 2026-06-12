---
title: "dvb-s, no scan for transport, dvbsm error"
date: 2009-04-19
forum: Mythbuntu
---

### Post by ringostare on 2009-04-19
Hello,
I'm using "jaunty beta" and I can not get transport scan in the backend setup for dvb-s transport. (Sorry for my English)
Here is the error message in the terminal :

```
2009-04-19 07:32:04.315 DVBSM(0), Warning: Can not count Uncorrected Blocks
                        eno: Function not implemented (38)
```

Any ideas ? Thanks

---

### Post by ian dobson on 2009-04-19
Hi,

Maybe have a look at using w_scan to create a channels.conf file that you can use to "seed" mythtv. The channel scanner in mythtv isn't the best.

Regards
Ian Dobson

---

### Post by ringostare on 2009-04-19
I tryed this. I created a channels.conf with "scan" (dvb-s), but when i try to use it in the setup, the scan find nothing.
here's my channels.conf :

```
TF1:11677:h:0:27500:165:100:206
France 2:12692:h:0:27500:162:88:503
France 3:12692:h:0:27500:182:196:538
France 4:12692:h:0:27500:183:198:539
France 5:11681:h:0:27500:175:144:217
M6  :12692:h:0:27500:160:80:501
ARTE:11623:v:0:27500:223:233:10703
DIRECT 8:12539:h:0:27500:5129:5130:8880
W9:12692:h:0:27500:163:92:504
NRJ12:12692:h:0:27500:161:84:502
NT1:11681:h:0:27500:168:112:209
RTL9:11677:h:0:27500:172:128:200
TMC:12692:h:0:27500:164:96:505
AB1:11677:h:0:27500:160:80:201
Virgin 17:12692:h:0:27500:168:112:509
TV5MONDE EUROPE:11137:h:0:27500:3522:3642:7322
TV8 Mt Blanc:12539:h:0:27500:5126:5127:8878
VIDEOCLICK:11677:h:0:27500:210:276:230
Gulli:12692:h:0:27500:173:132:513
MANGAS:11681:h:0:27500:170:120:211
ANIMAUX:11681:h:0:27500:162:88:203
ENCYCLOPEDIA:11681:h:0:27500:171:124:212
ESCALES:11681:h:0:27500:166:104:207
CHASSE & PECHE:11681:h:0:27500:163:92:204
AB MOTEURS:11681:h:0:27500:161:84:202
France ô:11681:h:0:27500:176:148:218
```

---

### Post by ian dobson on 2009-04-19
Hi,

Are you sure you're calling scan with the correct options. Scan can create vdr or xzap? compatible channel.conf file.

Here's part of my channels.conf file (DVB-C)

```
TVE Internacional(RTVE):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:3521:3522:35001
TV5MONDE(CANALSATELLITE):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:164:112:31209
RTPI(CANALSATELLITE):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:161:61:35201
TRT International((null)):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:712:713:38601
SLO-TV1(RTV Slovenija):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:200:201:36801
RAI2(RAI):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:513:651:32202
RTK-SAT(PRVDR):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:308:67:38201
HRT-TV1(OIV Zagreb):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:100:102:37601
CNBC Europe(CNBC):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:307:104:34001
ERTSAT Europe((null)):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:2101:2111:35401
BH-TV1((null)):394000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:101:53:38001
ANIXE HD(BetaDigital):570000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:1535:0:40401
arte HD(ZDFvision):570000000:INVERSION_AUTO:6900000:FEC_NONE:QAM_256:6210:6221:40402
```

Regards
Ian Dobson

---

### Post by ringostare on 2009-04-20
I see, but I don't find the good options to use for generate a channels.conf like yours. Any idea ?

And I wonder what is this "dvbsm" from my first post error message ? 

Thanks

---

### Post by ian dobson on 2009-04-20
Hi,

Have a look here [http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/) I think you need to use the -X option.

Regards
Ian Dobson

---

### Post by ringostare on 2009-04-20
Thanks but w_scan don't work for dvb-s, I need to use "scan" or "dvbscan".

---


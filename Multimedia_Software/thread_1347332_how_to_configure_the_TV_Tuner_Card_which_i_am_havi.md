---
title: "how to configure the TV Tuner Card which i am having SAA7134 / 7135 HL"
date: 2009-12-06
forum: Multimedia Software
---

### Post by kistareddyd on 2009-12-06
Plzz update my question to answer i am eagerly waiting for this..............

kistareddyd@kistareddyd-desktop:~$ lsmod | grep saa
saa7134_alsa           12128  1 
snd_pcm                75296  4 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
saa7134               152616  1 saa7134_alsa
ir_common              48512  1 saa7134
v4l2_common            17500  1 saa7134
videodev               36736  2 saa7134,v4l2_common
videobuf_dma_sg        12544  2 saa7134_alsa,saa7134
videobuf_core          17952  2 saa7134,videobuf_dma_sg
tveeprom               11872  1 saa7134
snd                    59204  15 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

above is my card details plzz explain me to watch tv in ubuntu 9.10 ........

Thank you...

---

### Post by xc3RnbFO8P on 2009-12-06
In Terminal show the output of:
> dmesg 

---

### Post by lovinglinux on 2009-12-06
[This](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2) is how I installed mine.

---

### Post by kistareddyd on 2009-12-07
This My Card info

kistareddyd@kistareddyd-desktop:~$ dmesg | grep saa7134
[   13.326752] saa7134 0000:05:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.326757] saa7134[0]: found at 0000:05:06.0, rev: 1, irq: 22, latency: 16, mmio: 0xfd7ff000
[   13.326762] saa7134: <rant>
[   13.326763] saa7134:  Congratulations!  Your TV card vendor saved a few
[   13.326763] saa7134:  cents for a eeprom, thus your pci board has no
[   13.326764] saa7134:  subsystem ID and I can't identify it automatically
[   13.326765] saa7134: </rant>
[   13.326766] saa7134: I feel better now.  Ok, here are the good news:
[   13.326767] saa7134: You can use the card=<nr> insmod option to specify
[   13.326767] saa7134: which board do you have.  The list:
[   13.326770] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   13.326772] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   13.326775] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   13.326778] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   13.326781] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   13.326784] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   13.326786] saa7134:   card=6 -> Tevion MD 9717                          
[   13.326788] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   13.326792] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   13.326794] saa7134:   card=9 -> Medion 5044                             
[   13.326796] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   13.326798] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   13.326801] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   13.326804] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   13.326806] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   13.326808] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   13.326811] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   13.326814] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   13.326817] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   13.326819] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   13.326822] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   13.326824] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   13.326827] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   13.326829] saa7134:   card=23 -> BMK MPEX Tuner                          
[   13.326831] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   13.326834] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   13.326836] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   13.326839] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   13.326841] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   13.326843] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   13.326845] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   13.326848] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   13.326850] saa7134:   card=32 -> AVACS SmartTV                           
[   13.326852] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   13.326855] saa7134:   card=34 -> Noval Prime TV 7133                     
[   13.326857] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   13.326859] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   13.326862] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   13.326864] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   13.326866] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   13.326870] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   13.326872] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   13.326875] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   13.326877] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   13.326879] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   13.326881] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   13.326883] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   13.326886] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   13.326888] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   13.326891] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   13.326893] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   13.326896] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   13.326898] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   13.326901] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   13.326903] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   13.326907] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   13.326911] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   13.326913] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   13.326916] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   13.326920] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   13.326922] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   13.326926] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   13.326928] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   13.326930] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   13.326932] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   13.326935] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   13.326937] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   13.326938] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   13.326941] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   13.326944] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   13.326946] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   13.326949] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   13.326951] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   13.326954] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   13.326956] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   13.326959] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   13.326961] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   13.326964] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   13.326966] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   13.326969] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   13.326971] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   13.326973] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   13.326976] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   13.326979] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   13.326981] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   13.326984] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   13.326987] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   13.326990] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   13.326992] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   13.326995] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   13.326997] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   13.327001] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   13.327003] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   13.327006] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   13.327008] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   13.327012] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   13.327015] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   13.327018] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   13.327021] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   13.327024] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   13.327027] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   13.327029] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   13.327032] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   13.327034] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   13.327036] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   13.327041] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   13.327044] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   13.327048] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   13.327050] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   13.327053] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   13.327055] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   13.327057] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   13.327060] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   13.327062] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   13.327065] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   13.327067] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   13.327070] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   13.327072] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   13.327075] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   13.327077] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   13.327080] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   13.327082] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   13.327085] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   13.327087] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   13.327090] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   13.327092] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   13.327095] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   13.327097] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   13.327100] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   13.327103] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   13.327105] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   13.327108] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   13.327110] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   13.327112] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   13.327114] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   13.327117] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   13.327119] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   13.327122] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   13.327125] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   13.327127] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   13.327130] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   13.327132] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   13.327135] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   13.327137] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   13.327140] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   13.327142] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   13.327145] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   13.327148] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   13.327150] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   13.327153] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   13.327155] saa7134:   card=150 -> Zogis Real Angel 220                    
[   13.327157] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   13.327160] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   13.327162] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   13.327165] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   13.327167] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   13.327170] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   13.327174] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   13.327177] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   13.327179] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   13.327182] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   13.327184] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   13.327186] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   13.327189] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   13.327191] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   13.327194] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   13.327197] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   13.327199] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   13.327202] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   13.327204] saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   13.327218] saa7134[0]: board init: gpio is c04000
[   13.327222] IRQ 22/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.428839] saa7134[0]: Huh, no eeprom present (err=-5)?
[   13.429458] saa7134[0]: registered device video0 [v4l2]
[   13.429477] saa7134[0]: registered device vbi0
[   13.433022] saa7134 ALSA driver for DMA sound loaded
[   13.433032] IRQ 22/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.433048] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 22 registered as card -2

---

### Post by kistareddyd on 2009-12-07
How to do frequency scan to get the channels

---

### Post by Rschnauzer on 2009-12-21
The packets w-scan and dvb-apps include scan utilities, it depends on your TV-App which format you need.
Which application are you using?

---

### Post by kistareddyd on 2010-12-04
I am Using tvtime

---


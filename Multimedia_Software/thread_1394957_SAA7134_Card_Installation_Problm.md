---
title: "SAA7134 Card Installation Problm"
date: 2010-01-31
forum: Multimedia Software
---

### Post by kistareddyd on 2010-01-31
Below i am giving my card details plzz reply me as soon as possible 
thanking you
---------------------------------

root@kistareddyd-desktop:~# dmesg | grep saa
[    4.920658] saa7130/34: v4l2 driver version 0.2.15 loaded
[    4.920709] saa7134 0000:05:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.920714] saa7134[0]: found at 0000:05:05.0, rev: 1, irq: 21, latency: 16, mmio: 0xfd7ff000
[    4.920718] saa7134: <rant>
[    4.920719] saa7134:  Congratulations!  Your TV card vendor saved a few
[    4.920719] saa7134:  cents for a eeprom, thus your pci board has no
[    4.920720] saa7134:  subsystem ID and I can't identify it automatically
[    4.920721] saa7134: </rant>
[    4.920721] saa7134: I feel better now.  Ok, here are the good news:
[    4.920722] saa7134: You can use the card=<nr> insmod option to specify
[    4.920723] saa7134: which board do you have.  The list:
[    4.920725] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[    4.920727] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[    4.920731] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[    4.920734] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[    4.920737] saa7134:   card=4 -> EMPRESS                                  1131:6752
[    4.920739] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[    4.920742] saa7134:   card=6 -> Tevion MD 9717                          
[    4.920744] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[    4.920747] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[    4.920749] saa7134:   card=9 -> Medion 5044                             
[    4.920751] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[    4.920753] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[    4.920756] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[    4.920759] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[    4.920761] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[    4.920763] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[    4.920766] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[    4.920769] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[    4.920772] saa7134:   card=18 -> BMK MPEX No Tuner                       
[    4.920774] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[    4.920776] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[    4.920779] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[    4.920781] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[    4.920784] saa7134:   card=23 -> BMK MPEX Tuner                          
[    4.920786] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[    4.920788] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[    4.920791] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[    4.920793] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[    4.920795] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[    4.920797] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[    4.920800] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[    4.920802] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[    4.920805] saa7134:   card=32 -> AVACS SmartTV                           
[    4.920807] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[    4.920809] saa7134:   card=34 -> Noval Prime TV 7133                     
[    4.920811] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[    4.920814] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[    4.920816] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[    4.920818] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[    4.920821] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[    4.920824] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[    4.920827] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[    4.920829] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[    4.920831] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[    4.920833] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[    4.920835] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[    4.920838] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[    4.920840] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[    4.920843] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[    4.920845] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[    4.920848] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[    4.920850] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[    4.920852] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[    4.920855] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[    4.920858] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[    4.920862] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[    4.920865] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[    4.920867] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[    4.920870] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[    4.920874] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[    4.920876] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[    4.920880] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[    4.920882] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[    4.920884] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[    4.920886] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[    4.920889] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[    4.920890] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[    4.920892] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[    4.920895] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[    4.920898] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[    4.920900] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[    4.920903] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[    4.920905] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[    4.920907] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[    4.920910] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[    4.920912] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[    4.920915] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[    4.920917] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[    4.920920] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[    4.920922] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[    4.920924] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[    4.920927] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[    4.920929] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[    4.920932] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[    4.920935] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[    4.920937] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[    4.920940] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[    4.920943] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[    4.920946] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[    4.920948] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[    4.920951] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[    4.920954] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[    4.920956] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[    4.920959] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[    4.920961] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[    4.920965] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[    4.920968] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[    4.920971] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[    4.920974] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[    4.920977] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[    4.920980] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[    4.920982] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[    4.920985] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[    4.920987] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[    4.920989] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[    4.920994] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[    4.920997] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[    4.921000] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[    4.921003] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[    4.921005] saa7134:   card=109 -> Philips Tiger - S Reference design      
[    4.921007] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[    4.921010] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[    4.921012] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[    4.921015] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[    4.921017] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[    4.921020] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[    4.921022] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[    4.921025] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[    4.921027] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[    4.921030] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[    4.921032] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[    4.921035] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[    4.921037] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[    4.921040] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[    4.921042] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[    4.921045] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[    4.921047] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[    4.921050] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[    4.921053] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[    4.921055] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[    4.921058] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[    4.921076] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[    4.921079] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[    4.921081] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[    4.921083] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[    4.921085] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[    4.921088] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[    4.921090] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[    4.921093] saa7134:   card=138 -> Avermedia M115                           1461:a836
[    4.921095] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[    4.921098] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[    4.921100] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[    4.921103] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[    4.921105] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[    4.921108] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[    4.921110] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[    4.921114] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[    4.921116] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[    4.921118] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[    4.921121] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[    4.921123] saa7134:   card=150 -> Zogis Real Angel 220                    
[    4.921125] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[    4.921128] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[    4.921130] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[    4.921133] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[    4.921135] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[    4.921138] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[    4.921142] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[    4.921144] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[    4.921147] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[    4.921149] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[    4.921152] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[    4.921154] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[    4.921157] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[    4.921159] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[    4.921162] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[    4.921164] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[    4.921167] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[    4.921169] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[    4.921172] saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[    4.921183] saa7134[0]: board init: gpio is c04000
[    4.921187] IRQ 21/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.024693] saa7134[0]: Huh, no eeprom present (err=-5)?
[    5.025296] saa7134[0]: registered device video0 [v4l2]
[    5.025313] saa7134[0]: registered device vbi0
[    6.504939] saa7134 ALSA driver for DMA sound loaded
[    6.504951] IRQ 21/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.504967] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 21 registered as card -2

how can i watch TV In Ubuntu 9.10 plzz let me knw installation and configuration details plzzz

---

### Post by kistareddyd on 2010-02-15
**Is no one knows about this problem ? **
> **kistareddyd said:**
> Below i am giving my card details plzz reply me as soon as possible 
thanking you
---------------------------------

root@kistareddyd-desktop:~# dmesg | grep saa
[    4.920658] saa7130/34: v4l2 driver version 0.2.15 loaded
[    4.920709] saa7134 0000:05:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.920714] saa7134[0]: found at 0000:05:05.0, rev: 1, irq: 21, latency: 16, mmio: 0xfd7ff000
[    4.920718] saa7134: <rant>
[    4.920719] saa7134:  Congratulations!  Your TV card vendor saved a few
[    4.920719] saa7134:  cents for a eeprom, thus your pci board has no
[    4.920720] saa7134:  subsystem ID and I can't identify it automatically
[    4.920721] saa7134: </rant>
[    4.920721] saa7134: I feel better now.  Ok, here are the good news:
[    4.920722] saa7134: You can use the card=<nr> insmod option to specify
[    4.920723] saa7134: which board do you have.  The list:
[    4.920725] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[    4.920727] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[    4.920731] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[    4.920734] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[    4.920737] saa7134:   card=4 -> EMPRESS                                  1131:6752
[    4.920739] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[    4.920742] saa7134:   card=6 -> Tevion MD 9717                          
[    4.920744] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[    4.920747] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[    4.920749] saa7134:   card=9 -> Medion 5044                             
[    4.920751] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[    4.920753] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[    4.920756] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[    4.920759] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[    4.920761] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[    4.920763] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[    4.920766] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[    4.920769] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[    4.920772] saa7134:   card=18 -> BMK MPEX No Tuner                       
[    4.920774] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[    4.920776] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[    4.920779] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[    4.920781] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[    4.920784] saa7134:   card=23 -> BMK MPEX Tuner                          
[    4.920786] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[    4.920788] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[    4.920791] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[    4.920793] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[    4.920795] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[    4.920797] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[    4.920800] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[    4.920802] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[    4.920805] saa7134:   card=32 -> AVACS SmartTV                           
[    4.920807] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[    4.920809] saa7134:   card=34 -> Noval Prime TV 7133                     
[    4.920811] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[    4.920814] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[    4.920816] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[    4.920818] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[    4.920821] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[    4.920824] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[    4.920827] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[    4.920829] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[    4.920831] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[    4.920833] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[    4.920835] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[    4.920838] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[    4.920840] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[    4.920843] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[    4.920845] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[    4.920848] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[    4.920850] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[    4.920852] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[    4.920855] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[    4.920858] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[    4.920862] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[    4.920865] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[    4.920867] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[    4.920870] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[    4.920874] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[    4.920876] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[    4.920880] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[    4.920882] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[    4.920884] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[    4.920886] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[    4.920889] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[    4.920890] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[    4.920892] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[    4.920895] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[    4.920898] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[    4.920900] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[    4.920903] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[    4.920905] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[    4.920907] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[    4.920910] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[    4.920912] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[    4.920915] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[    4.920917] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[    4.920920] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[    4.920922] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[    4.920924] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[    4.920927] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[    4.920929] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[    4.920932] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[    4.920935] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[    4.920937] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[    4.920940] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[    4.920943] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[    4.920946] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[    4.920948] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[    4.920951] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[    4.920954] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[    4.920956] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[    4.920959] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[    4.920961] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[    4.920965] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[    4.920968] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[    4.920971] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[    4.920974] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[    4.920977] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[    4.920980] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[    4.920982] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[    4.920985] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[    4.920987] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[    4.920989] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[    4.920994] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[    4.920997] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[    4.921000] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[    4.921003] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[    4.921005] saa7134:   card=109 -> Philips Tiger - S Reference design      
[    4.921007] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[    4.921010] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[    4.921012] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[    4.921015] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[    4.921017] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[    4.921020] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[    4.921022] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[    4.921025] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[    4.921027] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[    4.921030] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[    4.921032] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[    4.921035] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[    4.921037] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[    4.921040] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[    4.921042] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[    4.921045] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[    4.921047] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[    4.921050] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[    4.921053] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[    4.921055] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[    4.921058] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[    4.921076] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[    4.921079] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[    4.921081] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[    4.921083] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[    4.921085] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[    4.921088] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[    4.921090] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[    4.921093] saa7134:   card=138 -> Avermedia M115                           1461:a836
[    4.921095] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[    4.921098] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[    4.921100] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[    4.921103] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[    4.921105] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[    4.921108] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[    4.921110] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[    4.921114] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[    4.921116] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[    4.921118] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[    4.921121] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[    4.921123] saa7134:   card=150 -> Zogis Real Angel 220                    
[    4.921125] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[    4.921128] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[    4.921130] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[    4.921133] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[    4.921135] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[    4.921138] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[    4.921142] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[    4.921144] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[    4.921147] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[    4.921149] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[    4.921152] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[    4.921154] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[    4.921157] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[    4.921159] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[    4.921162] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[    4.921164] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[    4.921167] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[    4.921169] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[    4.921172] saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[    4.921183] saa7134[0]: board init: gpio is c04000
[    4.921187] IRQ 21/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    5.024693] saa7134[0]: Huh, no eeprom present (err=-5)?
[    5.025296] saa7134[0]: registered device video0 [v4l2]
[    5.025313] saa7134[0]: registered device vbi0
[    6.504939] saa7134 ALSA driver for DMA sound loaded
[    6.504951] IRQ 21/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.504967] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 21 registered as card -2

how can i watch TV In Ubuntu 9.10 plzz let me knw installation and configuration details plzzz

---


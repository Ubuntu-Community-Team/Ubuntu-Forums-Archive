---
title: "Ubuntu 12.04 - TV DVB tuner - SAA7134 - Specify card number - Help??"
date: 2013-05-20
forum: Multimedia Software
---

### Post by Albury_Boy on 2013-05-20
Hey,

I've got a Gigabyte branded TV DVB tuner which I'm trying to configure. 

Output of lspci is:
```
04:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

So, from doing some creative googleing, I figure that my options are either the SAA7133 or SAA7134 driver. I'm not sure how to specify which driver to use. Any assistance would be greatly appreciated.

When trying to scan for channels with w_scan,

```
w_scan -c AU -X > channels.conf
```

```
w_scan version 20111203 (compiled for DVB API 5.4)
using settings for AUSTRALIA
DVB aerial
DVB-T AU
frontend_type DVB-T, channellist 3
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
main:3079: FATAL: ***** NO USEABLE DVB-T CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
```

Output of ```
dmesg | grep saa7133 
```

```
[   21.483525] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 20, latency: 64, mmio: 0xfebff000
[   21.483760] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   21.484138] saa7133[0]: subsystem: 1458:9002, board: UNKNOWN/GENERIC [card=0,autodetected]
[   21.484180] saa7133[0]: board init: gpio is c000000
[   21.849597] saa7133[0]: i2c eeprom 00: 58 14 02 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   21.849607] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   21.849615] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c1 ff ff ff ff
[   21.849624] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849633] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 50 ff ff ff ff ff ff
[   21.849641] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849650] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849658] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849667] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849675] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849684] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849693] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849701] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849710] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849719] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849728] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.855101] saa7133[0]: registered device video0 [v4l2]
[   21.856736] saa7133[0]: registered device vbi0
[   21.867035] saa7133[0]/alsa: saa7133[0] at 0xfebff000 irq 20 registered as card -2
```


and output of ```
dmesg | grep saa7134
``` gives an amusing rant

```
[   21.483520] saa7134 0000:04:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.483530] saa7134: <rant>
[   21.483530] saa7134:  Congratulations!  Your TV card vendor saved a few
[   21.483531] saa7134:  cents for a eeprom, thus your pci board has no
[   21.483532] saa7134:  subsystem ID and I can't identify it automatically
[   21.483533] saa7134: </rant>
[   21.483533] saa7134: I feel better now.  Ok, here are the good news:
[   21.483534] saa7134: You can use the card=<nr> insmod option to specify
[   21.483535] saa7134: which board do you have.  The list:
[   21.483537] saa7134:   card=0 -> UNKNOWN/GENERIC
[   21.483540] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   21.483544] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   21.483547] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   21.483551] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   21.483553] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   21.483556] saa7134:   card=6 -> Tevion MD 9717
[   21.483558] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   21.483562] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   21.483565] saa7134:   card=9 -> Medion 5044
[   21.483567] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
[   21.483569] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   21.483572] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   21.483576] saa7134:   card=13 -> Typhoon TV+Radio 90031
[   21.483578] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   21.483581] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   21.483584] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   21.483588] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   21.483591] saa7134:   card=18 -> BMK MPEX No Tuner
[   21.483593] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   21.483596] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   21.483599] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   21.483602] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   21.483605] saa7134:   card=23 -> BMK MPEX Tuner
[   21.483607] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   21.483610] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   21.483613] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   21.483617] saa7134:   card=27 -> Manli MuchTV M-TV002
[   21.483619] saa7134:   card=28 -> Manli MuchTV M-TV001
[   21.483622] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   21.483625] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   21.483627] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   21.483630] saa7134:   card=32 -> AVACS SmartTV
[   21.483633] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   21.483635] saa7134:   card=34 -> Noval Prime TV 7133
[   21.483638] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   21.483641] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   21.483643] saa7134:   card=37 -> Items MuchTV Plus / IT-005
[   21.483646] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   21.483648] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   21.483652] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   21.483655] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   21.483658] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)
[   21.483660] saa7134:   card=43 -> :Zolid Xpert TV7134
[   21.483663] saa7134:   card=44 -> Empire PCI TV-Radio LE
[   21.483665] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   21.483668] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   21.483670] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   21.483673] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   21.483676] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   21.483679] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   21.483682] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   21.483685] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   21.483688] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   21.483690] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   21.483695] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   21.483699] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   21.483702] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   21.483705] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   21.483709] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[   21.483712] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   21.483716] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   21.483719] saa7134:   card=62 -> Compro VideoMate TV Gold+II
[   21.483721] saa7134:   card=63 -> Kworld Xpert TV PVR7134
[   21.483723] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   21.483726] saa7134:   card=65 -> V-Stream Studio TV Terminator
[   21.483728] saa7134:   card=66 -> Yuan TUN-900 (saa7135)
[   21.483731] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   21.483733] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   21.483736] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   21.483739] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   21.483742] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   21.483745] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   21.483748] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   21.483751] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   21.483754] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   21.483757] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   21.483760] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   21.483762] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   21.483765] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   21.483768] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   21.483770] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   21.483773] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   21.483777] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   21.483780] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   21.483782] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   21.483786] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   21.483789] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   21.483792] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   21.483795] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   21.483798] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   21.483801] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   21.483804] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   21.483807] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   21.483810] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   21.483814] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   21.483817] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   21.483821] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   21.483825] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   21.483828] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   21.483831] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   21.483833] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   21.483836] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   21.483839] saa7134:   card=103 -> Compro Videomate DVB-T200A
[   21.483841] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   21.483847] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   21.483850] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   21.483854] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   21.483857] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   21.483860] saa7134:   card=109 -> Philips Tiger - S Reference design
[   21.483863] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   21.483865] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   21.483868] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   21.483871] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   21.483874] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   21.483877] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   21.483880] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   21.483883] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   21.483886] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   21.483888] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   21.483891] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   21.483894] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   21.483897] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   21.483899] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   21.483902] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   21.483905] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   21.483908] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   21.483911] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   21.483914] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
[   21.483917] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   21.483920] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   21.483923] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   21.483926] saa7134:   card=132 -> Genius TVGO AM11MCE
[   21.483928] saa7134:   card=133 -> NXP Snake DVB-S reference design
[   21.483930] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   21.483933] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   21.483936] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   21.483939] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   21.483942] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   21.483945] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   21.483947] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   21.483950] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   21.483953] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   21.483956] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   21.483959] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   21.483962] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   21.483965] saa7134:   card=146 -> ASUSTeK P7131 Analog
[   21.483968] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   21.483970] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   21.483973] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   21.483976] saa7134:   card=150 -> Zogis Real Angel 220
[   21.483979] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   21.483981] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   21.483984] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   21.483987] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   21.484041] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   21.484045] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   21.484050] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   21.484052] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   21.484055] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   21.484058] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   21.484061] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   21.484064] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   21.484067] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   21.484069] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   21.484072] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   21.484075] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   21.484078] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   21.484081] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   21.484084] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   21.484086] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   21.484089] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   21.484092] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   21.484095] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   21.484098] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   21.484101] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
[   21.484104] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
[   21.484106] saa7134:   card=177 -> Hawell HW-404M7
[   21.484109] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
[   21.484111] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
[   21.484114] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
[   21.484118] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
[   21.484121] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
[   21.484124] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
[   21.484126] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
[   21.484129] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
[   21.484132] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
[   21.484135] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
[   21.867010] saa7134 ALSA driver for DMA sound loaded
```

---

### Post by Albury_Boy on 2013-05-20
**bump**

---

### Post by Albury_Boy on 2013-05-22
**bump bump**

Anyone?

---

### Post by vidtek on 2013-05-22
> **Albury_Boy said:**
> Hey,

I've got a Gigabyte branded TV DVB tuner which I'm trying to configure. 

Output of lspci is:
```
04:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

So, from doing some creative googleing, I figure that my options are either the SAA7133 or SAA7134 driver. I'm not sure how to specify which driver to use. Any assistance would be greatly appreciated.

When trying to scan for channels with w_scan,

```
w_scan -c AU -X > channels.conf
```

```
w_scan version 20111203 (compiled for DVB API 5.4)
using settings for AUSTRALIA
DVB aerial
DVB-T AU
frontend_type DVB-T, channellist 3
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
main:3079: FATAL: ***** NO USEABLE DVB-T CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.
```

Output of ```
dmesg | grep saa7133 
```

```
[   21.483525] saa7133[0]: found at 0000:04:01.0, rev: 209, irq: 20, latency: 64, mmio: 0xfebff000
[   21.483760] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   21.484138] saa7133[0]: subsystem: 1458:9002, board: UNKNOWN/GENERIC [card=0,autodetected]
[   21.484180] saa7133[0]: board init: gpio is c000000
[   21.849597] saa7133[0]: i2c eeprom 00: 58 14 02 90 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   21.849607] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   21.849615] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 c1 ff ff ff ff
[   21.849624] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849633] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 50 ff ff ff ff ff ff
[   21.849641] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849650] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849658] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849667] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849675] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849684] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849693] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849701] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849710] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849719] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.849728] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   21.855101] saa7133[0]: registered device video0 [v4l2]
[   21.856736] saa7133[0]: registered device vbi0
[   21.867035] saa7133[0]/alsa: saa7133[0] at 0xfebff000 irq 20 registered as card -2
```


and output of ```
dmesg | grep saa7134
``` gives an amusing rant

```
[   21.483520] saa7134 0000:04:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   21.483530] saa7134: <rant>
[   21.483530] saa7134:  Congratulations!  Your TV card vendor saved a few
[   21.483531] saa7134:  cents for a eeprom, thus your pci board has no
[   21.483532] saa7134:  subsystem ID and I can't identify it automatically
[   21.483533] saa7134: </rant>
[   21.483533] saa7134: I feel better now.  Ok, here are the good news:
[   21.483534] saa7134: You can use the card=<nr> insmod option to specify
[   21.483535] saa7134: which board do you have.  The list:
[   21.483537] saa7134:   card=0 -> UNKNOWN/GENERIC
[   21.483540] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   21.483544] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   21.483547] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   21.483551] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   21.483553] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   21.483556] saa7134:   card=6 -> Tevion MD 9717
[   21.483558] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   21.483562] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   21.483565] saa7134:   card=9 -> Medion 5044
[   21.483567] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
[   21.483569] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   21.483572] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   21.483576] saa7134:   card=13 -> Typhoon TV+Radio 90031
[   21.483578] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   21.483581] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   21.483584] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   21.483588] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   21.483591] saa7134:   card=18 -> BMK MPEX No Tuner
[   21.483593] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   21.483596] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   21.483599] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   21.483602] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   21.483605] saa7134:   card=23 -> BMK MPEX Tuner
[   21.483607] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   21.483610] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   21.483613] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   21.483617] saa7134:   card=27 -> Manli MuchTV M-TV002
[   21.483619] saa7134:   card=28 -> Manli MuchTV M-TV001
[   21.483622] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   21.483625] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   21.483627] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   21.483630] saa7134:   card=32 -> AVACS SmartTV
[   21.483633] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   21.483635] saa7134:   card=34 -> Noval Prime TV 7133
[   21.483638] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   21.483641] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   21.483643] saa7134:   card=37 -> Items MuchTV Plus / IT-005
[   21.483646] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   21.483648] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   21.483652] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   21.483655] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   21.483658] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)
[   21.483660] saa7134:   card=43 -> :Zolid Xpert TV7134
[   21.483663] saa7134:   card=44 -> Empire PCI TV-Radio LE
[   21.483665] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   21.483668] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   21.483670] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   21.483673] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   21.483676] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   21.483679] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   21.483682] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   21.483685] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   21.483688] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   21.483690] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   21.483695] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   21.483699] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   21.483702] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   21.483705] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   21.483709] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[   21.483712] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   21.483716] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   21.483719] saa7134:   card=62 -> Compro VideoMate TV Gold+II
[   21.483721] saa7134:   card=63 -> Kworld Xpert TV PVR7134
[   21.483723] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   21.483726] saa7134:   card=65 -> V-Stream Studio TV Terminator
[   21.483728] saa7134:   card=66 -> Yuan TUN-900 (saa7135)
[   21.483731] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   21.483733] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   21.483736] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   21.483739] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   21.483742] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   21.483745] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   21.483748] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   21.483751] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   21.483754] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   21.483757] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   21.483760] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   21.483762] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   21.483765] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   21.483768] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   21.483770] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   21.483773] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   21.483777] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   21.483780] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   21.483782] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   21.483786] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   21.483789] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   21.483792] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   21.483795] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   21.483798] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   21.483801] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   21.483804] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   21.483807] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   21.483810] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   21.483814] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   21.483817] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   21.483821] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   21.483825] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   21.483828] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   21.483831] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   21.483833] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   21.483836] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   21.483839] saa7134:   card=103 -> Compro Videomate DVB-T200A
[   21.483841] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   21.483847] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   21.483850] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   21.483854] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   21.483857] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   21.483860] saa7134:   card=109 -> Philips Tiger - S Reference design
[   21.483863] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   21.483865] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   21.483868] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   21.483871] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   21.483874] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   21.483877] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   21.483880] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   21.483883] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   21.483886] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   21.483888] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   21.483891] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   21.483894] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   21.483897] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   21.483899] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   21.483902] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   21.483905] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   21.483908] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   21.483911] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   21.483914] saa7134:   card=128 -> Beholder BeholdTV Columbus TV/FM         0000:5201
[   21.483917] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   21.483920] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   21.483923] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   21.483926] saa7134:   card=132 -> Genius TVGO AM11MCE
[   21.483928] saa7134:   card=133 -> NXP Snake DVB-S reference design
[   21.483930] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   21.483933] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   21.483936] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   21.483939] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   21.483942] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   21.483945] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   21.483947] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   21.483950] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   21.483953] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   21.483956] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   21.483959] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   21.483962] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   21.483965] saa7134:   card=146 -> ASUSTeK P7131 Analog
[   21.483968] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   21.483970] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   21.483973] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   21.483976] saa7134:   card=150 -> Zogis Real Angel 220
[   21.483979] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   21.483981] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   21.483984] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   21.483987] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   21.484041] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   21.484045] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   21.484050] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   21.484052] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   21.484055] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   21.484058] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   21.484061] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   21.484064] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   21.484067] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   21.484069] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   21.484072] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   21.484075] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   21.484078] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   21.484081] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   21.484084] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   21.484086] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   21.484089] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   21.484092] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   21.484095] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   21.484098] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   21.484101] saa7134:   card=175 -> Leadtek Winfast DTV1000S                 107d:6655
[   21.484104] saa7134:   card=176 -> Beholder BeholdTV 505 RDS                0000:5051
[   21.484106] saa7134:   card=177 -> Hawell HW-404M7
[   21.484109] saa7134:   card=178 -> Beholder BeholdTV H7                     5ace:7190
[   21.484111] saa7134:   card=179 -> Beholder BeholdTV A7                     5ace:7090
[   21.484114] saa7134:   card=180 -> Avermedia PCI M733A                      1461:4155 1461:4255
[   21.484118] saa7134:   card=181 -> TechoTrend TT-budget T-3000              13c2:2804
[   21.484121] saa7134:   card=182 -> Kworld PCI SBTVD/ISDB-T Full-Seg Hybrid  17de:b136
[   21.484124] saa7134:   card=183 -> Compro VideoMate Vista M1F               185b:c900
[   21.484126] saa7134:   card=184 -> Encore ENLTV-FM 3                        1a7f:2108
[   21.484129] saa7134:   card=185 -> MagicPro ProHDTV Pro2 DMB-TH/Hybrid      17de:d136
[   21.484132] saa7134:   card=186 -> Beholder BeholdTV 501                    5ace:5010
[   21.484135] saa7134:   card=187 -> Beholder BeholdTV 503 FM                 5ace:5030
[   21.867010] saa7134 ALSA driver for DMA sound loaded
```

Alburyboy-

These cards are problematic, the best support comes from the driver which was written by Steven Toth for the Hauppauge branded tuners.  Unfortunately there are literally hundreds of variants of this chipset as the above shows.
Here's what you can try:
```

sudo gedit /etc/modprobe.d/options.conf

```
(or whatever editor you prefer)

place this one line in the file and save it.
```

options saa7164 card=x#

```
*x = your card's number*

Reboot and check to see if it is listed correctly.

Best of luck, Tony.

---

### Post by Albury_Boy on 2013-05-23
Thanks for the tip Tony. You answered one of the big things that was stumping me, which was defining which driver the PCI should use at - [COLOR=#000000][FONT=Ubuntu Mono]/etc/modprobe.d/options.conf[/FONT][/COLOR]

However... I get no output for [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep saa7164[/FONT][/COLOR]  

Do I need to compile the driver from source? Is there a package for this? Is it a binary blob or something? I had a look around some other forum posts regarding this driver and found a link, but it was broken. Am I looking at the problem from the wrong angle? 

One thing I find funny about this is: I was watching Bryan Landuke's 2013 "Why Linux Sucks" earlier ([http://www.youtube.com/watch?v=QKwWPQ1Orzs](http://www.youtube.com/watch?v=QKwWPQ1Orzs)), and one of the things he said was that driver problems are now fixed in Linux ;-)[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by vidtek on 2013-05-23
> **Albury_Boy said:**
> Thanks for the tip Tony. You answered one of the big things that was stumping me, which was defining which driver the PCI should use at - [COLOR=#000000][FONT=Ubuntu Mono]/etc/modprobe.d/options.conf[/FONT][/COLOR]

However... I get no output for [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep saa7164[/FONT][/COLOR]  

Do I need to compile the driver from source? Is there a package for this? Is it a binary blob or something? I had a look around some other forum posts regarding this driver and found a link, but it was broken. Am I looking at the problem from the wrong angle? 

One thing I find funny about this is: I was watching Bryan Landuke's 2013 "Why Linux Sucks" earlier ([http://www.youtube.com/watch?v=QKwWPQ1Orzs](http://www.youtube.com/watch?v=QKwWPQ1Orzs)), and one of the things he said was that driver problems are now fixed in Linux ;-)[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

Albury_boy-

I don't understand, you say you get nothing from the "dmesg | grep saa"  but in your first post there is a full return from it???

Don't forget, the Linux community is an all volounteer affair, the hardware manufacturers of most hardware types can hardly be bothered to write a driver for Windows, they sure as hell 'aint going to write them for the 10% or so Linux users.  The drivers we have in Linux are mostly reverse-engineered by some very clever people donating their time - just like Steven Toth.

Since the release of 11.04 all newer kernels have inbuilt drivers for many saa based cards, but there are many which don't.  I happen to have a Hauppauge 2200 which has a revision number not supported, I've literally spent days trying to get it to work and have given up.

Best regards, Tony

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Multimedia & Video**.*

---

### Post by Albury_Boy on 2013-05-24
Tony,

Might have been a typo there. I showed the output of saa71_3_4, you said saa71_6_4.

I'll work my way through the list of saa7134 cards to see if I can get one to work. I've tried three so far with no luck. I've also been working headless with ssh and the MythTV backend in a browser. I might plug a monitor into my server and do it directly to see if that makes a difference. 

Thanks again for your help with this.

---

### Post by vidtek on 2013-05-30
> **Albury_Boy said:**
> Tony,

Might have been a typo there. I showed the output of saa71_3_4, you said saa71_6_4.

I'll work my way through the list of saa7134 cards to see if I can get one to work. I've tried three so far with no luck. I've also been working headless with ssh and the MythTV backend in a browser. I might plug a monitor into my server and do it directly to see if that makes a difference. 

Thanks again for your help with this.

Albury_boy

Sorry taken so long to get back to you.  The 7134 and 7164 are very similar, the steps required pretty much the same for both.  I've been struggling with
a 7164 card with issues as a rev2 variant showing corrupt image  error at boottime and dmesg, Steven Toth wrote a patch and I finally got it working today after 6 months of intermittently trying.  
Working headless is an exercise in sheer frustration with these issues, why would you even consider doing it that way?  You must be even more of a masochist than me!
All the best Tony

---


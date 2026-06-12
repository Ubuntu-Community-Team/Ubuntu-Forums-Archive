---
title: "How to add tuner card SBT-TVFM"
date: 2009-07-09
forum: Multimedia Software
---

### Post by jerez76 on 2009-07-09
$ lspci | grep Multimedia
07:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
07:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

$ sudo apt-get install xawtv
$ sudo apt-get install tvtime
$ sudo gedit /etc/modprobe.d/bttv 
note: file doesnt exist

add to bttv file one liner 

options bttv card=142 tuner=68 radio=1

$ sudo dmesg -c
$ sudo modprobe -r bttv
$ sudo modprobe bttv

$ dmesg | grep bt
[   17.444624] bttv: driver version 0.9.17 loaded
[   17.444627] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.444674] bttv: Bt8xx card found (0).
[   17.444685] bttv 0000:07:06.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   17.444695] bttv0: Bt878 (rev 17) at 0000:07:06.0, irq: 23, latency: 16, mmio: 0xfd4ff000
[   17.444719] bttv0: using: Sabrent TV-FM (bttv version) [card=142,insmod option]
[   17.444744] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[   17.444783] bttv0: tuner type=68
[   17.537696] tuner' 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   17.546909] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   17.555425] bttv0: registered device video0
[   17.555449] bttv0: registered device vbi0
[   17.555470] bttv0: registered device radio0
[   17.555491] bttv0: PLL: 28636363 => 35468950 .. ok
[  104.130987] bttv0: PLL can sleep, using XTAL (28636363).
[  485.592007] bttv0: timeout: drop=862 irq=33243/38123, risc=304d705c, bits: HSYNC OFLOW FDSR
[ 1645.984237] bttv0: reset, reinitialize
[ 1645.984267] bttv0: PLL can sleep, using XTAL (28636363).

$ sudo xawtv -hwscan 
$ sudo xawtv -device /dev/video0
it should start working 

if you get a permission denied on video0 it maybe zombied just reboot. kill -9, killall,sysmon kill process still leaves zombied video0. I think it is because the card isn't really shut off completely just the app. for example, if you got audio out and plug it in audio in and close xawtv then you will still have sound. 

I've tried tuner=2 for NTSC it didnt really work for me . 68 is dual NTSC/ATSC which works.

TV card list 
[http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.bttv)

Tuner codes 

tuner=0 - Temic PAL (4002 FH5)
tuner=1 - Philips PAL_I (FI1246 and compatibles)
tuner=2 - Philips NTSC (FI1236,FM1236 and compatibles)
tuner=3 - Philips (SECAM+PAL_BG) (FI1216MF, FM1216MF, FR1216MF)
tuner=4 - NoTuner
tuner=5 - Philips PAL_BG (FI1216 and compatibles)
tuner=6 - Temic NTSC (4032 FY5)
tuner=7 - Temic PAL_I (4062 FY5)
tuner=8 - Temic NTSC (4036 FY5)
tuner=9 - Alps HSBH1
tuner=10 - Alps TSBE1
tuner=11 - Alps TSBB5
tuner=12 - Alps TSBE5
tuner=13 - Alps TSBC5
tuner=14 - Temic PAL_BG (4006FH5)
tuner=15 - Alps TSCH6
tuner=16 - Temic PAL_DK (4016 FY5)
tuner=17 - Philips NTSC_M (MK2)
tuner=18 - Temic PAL_I (4066 FY5)
tuner=19 - Temic PAL* auto (4006 FN5)
tuner=20 - Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5)
tuner=21 - Temic NTSC (4039 FR5)
tuner=22 - Temic PAL/SECAM multi (4046 FM5)
tuner=23 - Philips PAL_DK (FI1256 and compatibles)
tuner=24 - Philips PAL/SECAM multi (FQ1216ME)
tuner=25 - LG PAL_I+FM (TAPC-I001D)
tuner=26 - LG PAL_I (TAPC-I701D)
tuner=27 - LG NTSC+FM (TPI8NSR01F)
tuner=28 - LG PAL_BG+FM (TPI8PSB01D)
tuner=29 - LG PAL_BG (TPI8PSB11D)
tuner=30 - Temic PAL* auto + FM (4009 FN5)
tuner=31 - SHARP NTSC_JP (2U5JF5540)
tuner=32 - Samsung PAL TCPM9091PD27
tuner=33 - MT20xx universal
tuner=34 - Temic PAL_BG (4106 FH5)
tuner=35 - Temic PAL_DK/SECAM_L (4012 FY5)
tuner=36 - Temic NTSC (4136 FY5)
tuner=37 - LG PAL (newer TAPC series)
tuner=38 - Philips PAL/SECAM multi (FM1216ME MK3)
tuner=39 - LG NTSC (newer TAPC series)
tuner=40 - HITACHI V7-J180AT
tuner=41 - Philips PAL_MK (FI1216 MK)
tuner=42 - Philips FCV1236D ATSC/NTSC dual in
tuner=43 - Philips NTSC MK3 (FM1236MK3 or FM1236/F)
tuner=44 - Philips 4 in 1 (ATI TV Wonder Pro/Conexant)
tuner=45 - Microtune 4049 FM5
tuner=46 - Panasonic VP27s/ENGE4324D
tuner=47 - LG NTSC (TAPE series)
tuner=48 - Tenna TNF 8831 BGFF)
tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in
tuner=50 - TCL 2002N
tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
tuner=52 - Thomson DTT 7610 (ATSC/NTSC)
tuner=53 - Philips FQ1286
tuner=54 - Philips/NXP TDA 8290/8295 + 8275/8275A/18271
tuner=55 - TCL 2002MB
tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
tuner=57 - Philips FQ1236A MK4
tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
tuner=59 - Ymec TVision TVF-5533MF
tuner=60 - Thomson DTT 761X (ATSC/NTSC)
tuner=61 - Tena TNF9533-D/IF/TNF9533-B/DF
tuner=62 - Philips TEA5767HN FM Radio
tuner=63 - Philips FMD1216ME MK3 Hybrid Tuner
tuner=64 - LG TDVS-H06xF
tuner=65 - Ymec TVF66T5-B/DFF
tuner=66 - LG TALN series
tuner=67 - Philips TD1316 Hybrid Tuner
tuner=68 - Philips TUV1236D ATSC/NTSC dual in
tuner=69 - Tena TNF 5335 and similar models
tuner=70 - Samsung TCPN 2121P30A
tuner=71 - Xceive xc2028/xc3028 tuner
tuner=72 - Thomson FE6600
tuner=73 - Samsung TCPG 6121P30A
tuner=75 - Philips TEA5761 FM Radio
tuner=76 - Xceive 5000 tuner
Cards cx88

0 -> UNKNOWN/GENERIC
  1 -> Hauppauge WinTV 34xxx models                        [0070:3400,0070:3401]
  2 -> GDI Black Gold                                      [14c7:0106,14c7:0107]
  3 -> PixelView                                           [1554:4811]
  4 -> ATI TV Wonder Pro                                   [1002:00f8]
  5 -> Leadtek Winfast 2000XP Expert                       [107d:6611,107d:6613]
  6 -> AverTV Studio 303 (M126)                            [1461:000b]
  7 -> MSI TV-@nywhere Master                              [1462:8606]
  8 -> Leadtek Winfast DV2000                              [107d:6620]
  9 -> Leadtek PVR 2000                                    [107d:663b,107d:663c,107d:6632]
 10 -> IODATA GV-VCP3/PCI                                  [10fc:d003]
 11 -> Prolink PlayTV PVR
 12 -> ASUS PVR-416                                        [1043:4823,1461:c111]
 13 -> MSI TV-@nywhere
 14 -> KWorld/VStream XPert DVB-T                          [17de:08a6]
 15 -> DViCO FusionHDTV DVB-T1                             [18ac:db00]
 16 -> KWorld LTV883RF
 17 -> DViCO FusionHDTV 3 Gold-Q                           [18ac:d810,18ac:d800]
 18 -> Hauppauge Nova-T DVB-T                              [0070:9002,0070:9001,0070:9000]
 19 -> Conexant DVB-T reference design                     [14f1:0187]
 20 -> Provideo PV259                                      [1540:2580]
 21 -> DViCO FusionHDTV DVB-T Plus                         [18ac:db10,18ac:db11]
 22 -> pcHDTV HD3000 HDTV                                  [7063:3000]
 23 -> digitalnow DNTV Live! DVB-T                         [17de:a8a6]
 24 -> Hauppauge WinTV 28xxx (Roslyn) models               [0070:2801]
 25 -> Digital-Logic MICROSPACE Entertainment Center (MEC) [14f1:0342]
 26 -> IODATA GV/BCTV7E                                    [10fc:d035]
 27 -> PixelView PlayTV Ultra Pro (Stereo)
 28 -> DViCO FusionHDTV 3 Gold-T                           [18ac:d820]
 29 -> ADS Tech Instant TV DVB-T PCI                       [1421:0334]
 30 -> TerraTec Cinergy 1400 DVB-T                         [153b:1166]
 31 -> DViCO FusionHDTV 5 Gold                             [18ac:d500]
 32 -> AverMedia UltraTV Media Center PCI 550              [1461:8011]
 33 -> Kworld V-Stream Xpert DVD
 34 -> ATI HDTV Wonder                                     [1002:a101]
 35 -> WinFast DTV1000-T                                   [107d:665f]
 36 -> AVerTV 303 (M126)                                   [1461:000a]
 37 -> Hauppauge Nova-S-Plus DVB-S                         [0070:9201,0070:9202]
 38 -> Hauppauge Nova-SE2 DVB-S                            [0070:9200]
 39 -> KWorld DVB-S 100                                    [17de:08b2,1421:0341]
 40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid                [0070:9400,0070:9402]
 41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)  [0070:9800,0070:9802]
 42 -> digitalnow DNTV Live! DVB-T Pro                     [1822:0025,1822:0019]
 43 -> KWorld/VStream XPert DVB-T with cx22702             [17de:08a1,12ab:2300]
 44 -> DViCO FusionHDTV DVB-T Dual Digital                 [18ac:db50,18ac:db54]
 45 -> KWorld HardwareMpegTV XPert                         [17de:0840,1421:0305]
 46 -> DViCO FusionHDTV DVB-T Hybrid                       [18ac:db40,18ac:db44]
 47 -> pcHDTV HD5500 HDTV                                  [7063:5500]
 48 -> Kworld MCE 200 Deluxe                               [17de:0841]
 49 -> PixelView PlayTV P7000                              [1554:4813]
 50 -> NPG Tech Real TV FM Top 10                          [14f1:0842]
 51 -> WinFast DTV2000 H                                   [107d:665e]
 52 -> Geniatech DVB-S                                     [14f1:0084]
 53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T  [0070:1404,0070:1400,0070:1401,0070:1402]
 54 -> Norwood Micro TV Tuner
 55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM  [c180:c980]
 56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder   [0070:9600,0070:9601,0070:9602]
 57 -> ADS Tech Instant Video PCI                          [1421:0390]
 58 -> Pinnacle PCTV HD 800i                               [11bd:0051]
 59 -> DViCO FusionHDTV 5 PCI nano                         [18ac:d530]
 60 -> Pinnacle Hybrid PCTV                                [12ab:1788]
 61 -> Winfast TV2000 XP Global                            [107d:6f18]
 62 -> PowerColor RA330                                    [14f1:ea3d]
 63 -> Geniatech X8000-MT DVBT                             [14f1:8852]
 64 -> DViCO FusionHDTV DVB-T PRO                          [18ac:db30]
 65 -> DViCO FusionHDTV 7 Gold                             [18ac:d610]
 66 -> Prolink Pixelview MPEG 8000GT                       [1554:4935]
 67 -> Kworld PlusTV HD PCI 120 (ATSC 120)                 [17de:08c1]
Card saa7134
  
0 -> UNKNOWN/GENERIC
  1 -> Proteus Pro [philips reference design]   [1131:2001,1131:2001]
  2 -> LifeView FlyVIDEO3000                    [5168:0138,4e42:0138]
  3 -> LifeView/Typhoon FlyVIDEO2000            [5168:0138,4e42:0138]
  4 -> EMPRESS                                  [1131:6752]
  5 -> SKNet Monster TV                         [1131:4e85]
  6 -> Tevion MD 9717
  7 -> KNC One TV-Station RDS / Typhoon TV Tuner RDS [1131:fe01,1894:fe01]
  8 -> Terratec Cinergy 400 TV                  [153b:1142]
  9 -> Medion 5044
 10 -> Kworld/KuroutoShikou SAA7130-TVPCI
 11 -> Terratec Cinergy 600 TV                  [153b:1143]
 12 -> Medion 7134                              [16be:0003]
 13 -> Typhoon TV+Radio 90031
 14 -> ELSA EX-VISION 300TV                     [1048:226b]
 15 -> ELSA EX-VISION 500TV                     [1048:226a]
 16 -> ASUS TV-FM 7134                          [1043:4842,1043:4830,1043:4840]
 17 -> AOPEN VA1000 POWER                       [1131:7133]
 18 -> BMK MPEX No Tuner
 19 -> Compro VideoMate TV                      [185b:c100]
 20 -> Matrox CronosPlus                        [102B:48d0]
 21 -> 10MOONS PCI TV CAPTURE CARD              [1131:2001]
 22 -> AverMedia M156 / Medion 2819             [1461:a70b]
 23 -> BMK MPEX Tuner
 24 -> KNC One TV-Station DVR                   [1894:a006]
 25 -> ASUS TV-FM 7133                          [1043:4843]
 26 -> Pinnacle PCTV Stereo (saa7134)           [11bd:002b]
 27 -> Manli MuchTV M-TV002
 28 -> Manli MuchTV M-TV001
 29 -> Nagase Sangyo TransGear 3000TV           [1461:050c]
 30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card(PAL-BG,FM)  [1019:4cb4]
 31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card (NTSC,FM) [1019:4cb5]
 32 -> AVACS SmartTV
 33 -> AVerMedia DVD EZMaker                    [1461:10ff]
 34 -> Noval Prime TV 7133
 35 -> AverMedia AverTV Studio 305              [1461:2115]
 36 -> UPMOST PURPLE TV                         [12ab:0800]
 37 -> Items MuchTV Plus / IT-005
 38 -> Terratec Cinergy 200 TV                  [153b:1152]
 39 -> LifeView FlyTV Platinum Mini             [5168:0212,4e42:0212]
 40 -> Compro VideoMate TV PVR/FM               [185b:c100]
 41 -> Compro VideoMate TV Gold+                [185b:c100]
 42 -> Sabrent SBT-TVFM (saa7130)
 43 -> :Zolid Xpert TV7134
 44 -> Empire PCI TV-Radio LE
 45 -> Avermedia AVerTV Studio 307              [1461:9715]
 46 -> AVerMedia Cardbus TV/Radio (E500)        [1461:d6ee]
 47 -> Terratec Cinergy 400 mobile              [153b:1162]
 48 -> Terratec Cinergy 600 TV MK3              [153b:1158]
 49 -> Compro VideoMate Gold+ Pal               [185b:c200]
 50 -> Pinnacle PCTV 300i DVB-T + PAL           [11bd:002d]
 51 -> ProVideo PV952                           [1540:9524]
 52 -> AverMedia AverTV/305                     [1461:2108]
 53 -> ASUS TV-FM 7135                          [1043:4845]
 54 -> LifeView FlyTV Platinum FM / Gold        [5168:0214,5168:5214,1489:0214,5168:0304]
 55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere Duo [5168:0306,4E42:0306]
 56 -> Avermedia AVerTV 307                     [1461:a70a]
 57 -> Avermedia AVerTV GO 007 FM               [1461:f31f]
 58 -> ADS Tech Instant TV (saa7135)            [1421:0350,1421:0351,1421:0370,1421:1370]
 59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
 60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Cardbus [5168:0502,4e42:0502,1489:0502]
 61 -> Philips TOUGH DVB-T reference design     [1131:2004]
 62 -> Compro VideoMate TV Gold+II
 63 -> Kworld Xpert TV PVR7134
 64 -> FlyTV mini Asus Digimatrix               [1043:0210]
 65 -> V-Stream Studio TV Terminator
 66 -> Yuan TUN-900 (saa7135)
 67 -> Beholder BeholdTV 409 FM                 [0000:4091]
 68 -> GoTView 7135 PCI                         [5456:7135]
 69 -> Philips EUROPA V3 reference design       [1131:2004]
 70 -> Compro Videomate DVB-T300                [185b:c900]
 71 -> Compro Videomate DVB-T200                [185b:c901]
 72 -> RTD Embedded Technologies VFG7350        [1435:7350]
 73 -> RTD Embedded Technologies VFG7330        [1435:7330]
 74 -> LifeView FlyTV Platinum Mini2            [14c0:1212]
 75 -> AVerMedia AVerTVHD MCE A180              [1461:1044]
 76 -> SKNet MonsterTV Mobile                   [1131:4ee9]
 77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     [11bd:002e]
 78 -> ASUSTeK P7131 Dual                       [1043:4862,1043:4857]
 79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B)
 80 -> ASUS Digimatrix TV                       [1043:0210]
 81 -> Philips Tiger reference design           [1131:2018]
 82 -> MSI TV@Anywhere plus                     [1462:6231,1462:8624]
 83 -> Terratec Cinergy 250 PCI TV              [153b:1160]
 84 -> LifeView FlyDVB Trio                     [5168:0319]
 85 -> AverTV DVB-T 777                         [1461:2c05,1461:2c05]
 86 -> LifeView FlyDVB-T / Genius VideoWonder DVB-T [5168:0301,1489:0301]
 87 -> ADS Instant TV Duo Cardbus PTV331        [0331:1421]
 88 -> Tevion/KWorld DVB-T 220RF                [17de:7201]
 89 -> ELSA EX-VISION 700TV                     [1048:226c]
 90 -> Kworld ATSC110/115                       [17de:7350,17de:7352]
 91 -> AVerMedia A169 B                         [1461:7360]
 92 -> AVerMedia A169 B1                        [1461:6360]
 93 -> Medion 7134 Bridge #2                    [16be:0005]
 94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV @nywhere A/D NB [5168:3306,5168:3502,5168:3307,4e42:3502]
 95 -> LifeView FlyVIDEO3000 (NTSC)             [5169:0138]
 96 -> Medion Md8800 Quadro                     [16be:0007,16be:0008,16be:000d]
 97 -> LifeView FlyDVB-S /Acorp TV134DS         [5168:0300,4e42:0300]
 98 -> Proteus Pro 2309                         [0919:2003]
 99 -> AVerMedia TV Hybrid A16AR                [1461:2c00]
100 -> Asus Europa2 OEM                         [1043:4860]
101 -> Pinnacle PCTV 310i                       [11bd:002f]
102 -> Avermedia AVerTV Studio 507              [1461:9715]
103 -> Compro Videomate DVB-T200A
104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     [0070:6700,0070:6701,0070:6702,0070:6703,0070:6704,0070:6705]
105 -> Terratec Cinergy HT PCMCIA               [153b:1172]
106 -> Encore ENLTV                             [1131:2342,1131:2341,3016:2344]
107 -> Encore ENLTV-FM                          [1131:230f]
108 -> Terratec Cinergy HT PCI                  [153b:1175]
109 -> Philips Tiger - S Reference design
110 -> Avermedia M102                           [1461:f31e]
111 -> ASUS P7131 4871                          [1043:4871]
112 -> ASUSTeK P7131 Hybrid                     [1043:4876]
113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card (PAL,FM) [1019:4cb6]
114 -> KWorld DVB-T 210                         [17de:7250]
115 -> Sabrent PCMCIA TV-PCB05                  [0919:2003]
116 -> 10MOONS TM300 TV Card                    [1131:2304]
117 -> Avermedia Super 007                      [1461:f01d]
118 -> Beholder BeholdTV 401                    [0000:4016]
119 -> Beholder BeholdTV 403                    [0000:4036]
120 -> Beholder BeholdTV 403 FM                 [0000:4037]
121 -> Beholder BeholdTV 405                    [0000:4050]
122 -> Beholder BeholdTV 405 FM                 [0000:4051]
123 -> Beholder BeholdTV 407                    [0000:4070]
124 -> Beholder BeholdTV 407 FM                 [0000:4071]
125 -> Beholder BeholdTV 409                    [0000:4090]
126 -> Beholder BeholdTV 505 FM/RDS             [0000:5051,0000:505B,5ace:5050]
127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV 509 FM [0000:5071,0000:507B,5ace:5070,5ace:5090]
128 -> Beholder BeholdTV Columbus TVFM          [0000:5201]
129 -> Beholder BeholdTV 607 / BeholdTV 609 [5ace:6070,5ace:6071,5ace:6072,5ace:6073,5ace:6090,5ace:6091,5ace:6092,5ace:6093
]
130 -> Beholder BeholdTV M6 / BeholdTV M6 Extra [5ace:6190,5ace:6193,5ace:6191]
131 -> Twinhan Hybrid DTV-DVB 3056 PCI          [1822:0022]
132 -> Genius TVGO AM11MCE
133 -> NXP Snake DVB-S reference design
134 -> Medion/Creatix CTX953 Hybrid             [16be:0010]
135 -> MSI TV@nywhere A/D v1.1                  [1462:8625]
136 -> AVerMedia Cardbus TV/Radio (E506R)       [1461:f436]
137 -> AVerMedia Hybrid TV/Radio (A16D)         [1461:f936]
138 -> Avermedia M115                           [1461:a836]
139 -> Compro VideoMate T750                    [185b:c900]
140 -> Avermedia DVB-S Pro A700                 [1461:a7a1]
141 -> Avermedia DVB-S Hybrid+FM A700           [1461:a7a2]
142 -> Beholder BeholdTV H6                     [5ace:6290]

---

### Post by jerez76 on 2009-07-09
if you dont get anything just edit the bttv file with card and tuner listed 
and just repeat starting from modprobe -r bttv/ modprobe bttv

---

### Post by cagethis on 2009-08-11
$ lspci | grep Multimedia
02:04.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:04.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)


How do i make it so that I can use this card to capture video and sound 
thanks 
bill

---

### Post by avacado on 2009-10-08
Bill

We are working on the same problem with different hardware.
I am using a DVICO hybrid DVB-T tuner Card which will allegedly work 'out of the box' but I think this is an exageration even with the supplied windows drivers the software was terrible, but this is the last piece of the jigsaw, everything else works so much better in ubuntu, even without the card I am staying linux.

Now to business, have you made any progress? Are you watching telly on your PC?

---


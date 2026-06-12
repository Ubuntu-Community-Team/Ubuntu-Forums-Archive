---
title: "How do you setup the driver for a Philips based TV capture card?"
date: 2011-01-04
forum: Multimedia Software
---

### Post by ricardorios on 2011-01-04
Hi, I have a TV card that I have not managed to  install with Ubuntu 10.10 i386. I have tried various topics in various  forums and I could not install it.
  I hope you can help me to install it thank you.
  **lspci**

  01:07.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
 **dmesg**

  [10299.516344] saa7134 ALSA driver for DMA sound unloaded
[11385.340661] Linux video capture interface: v2.00
[11385.384278] saa7130/34: v4l2 driver version 0.2.16 loaded
[11385.384390] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 17, latency: 32, mmio: 0x0
[11385.384403] saa7130[0]: subsystem: 1131:0000, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]
[11385.384412] saa7130[0]: can't get MMIO memory @ 0x0
[11385.384431] saa7134: probe of 0000:01:07.0 failed with error -16
[11385.401174] saa7134 ALSA driver for DMA sound loaded
[11385.401182] saa7134 ALSA: no saa7134 cards found
[11477.797019] tvtime[12534]: segfault at 6b0 ip 0804cf64 sp bf928a4c error 4 in tvtime[8048000+76000]
[11626.141821] tvtime[12549]: segfault at 6b0 ip 0804cf64 sp bfec357c error 4 in tvtime[8048000+76000]
[12218.120632] saa7134 ALSA driver for DMA sound unloaded
[12464.993061] Linux video capture interface: v2.00
[12465.028285] saa7130/34: v4l2 driver version 0.2.16 loaded
[12465.028392] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 17, latency: 32, mmio: 0x0
[12465.028404] saa7134: <rant>
[12465.028406] saa7134: Congratulations! Your TV card vendor saved a few
[12465.028408] saa7134: cents for a eeprom, thus your pci board has no
[12465.028411] saa7134: subsystem ID and I can't identify it automatically
[12465.028414] saa7134: </rant>
[12465.028416] saa7134: I feel better now. Ok, here are the good news:
[12465.028418] saa7134: You can use the card=<nr> insmod option to specify
[12465.028421] saa7134: which board do you have. The list:
[12465.028428] saa7134: card=0 -> UNKNOWN/GENERIC
[12465.028435] saa7134: card=1 -> Proteus Pro [philips reference design] 1131:2001 1131:2001
[12465.028447] saa7134: card=2 -> LifeView FlyVIDEO3000 5168:0138 4e42:0138
[12465.028457] saa7134: card=3 -> LifeView/Typhoon FlyVIDEO2000 5168:0138 4e42:0138
[12465.028467] saa7134: card=4 -> EMPRESS 1131:6752
[12465.028475] saa7134: card=5 -> SKNet Monster TV 1131:4e85
[12465.028484] saa7134: card=6 -> Tevion MD 9717
[12465.028491] saa7134: card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[12465.028501] saa7134: card=8 -> Terratec Cinergy 400 TV 153b:1142
[12465.028510] saa7134: card=9 -> Medion 5044
[12465.028517] saa7134: card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
[12465.028523] saa7134: card=11 -> Terratec Cinergy 600 TV 153b:1143
[12465.028532] saa7134: card=12 -> Medion 7134 16be:0003 16be:5000
[12465.028542] saa7134: card=13 -> Typhoon TV+Radio 90031
[12465.028548] saa7134: card=14 -> ELSA EX-VISION 300TV 1048:226b
[12465.028557] saa7134: card=15 -> ELSA EX-VISION 500TV 1048:226a
[12465.028565] saa7134: card=16 -> ASUS TV-FM 7134 1043:4842 1043:4830 1043:4840
[12465.028576] saa7134: card=17 -> AOPEN VA1000 POWER 1131:7133
[12465.028585] saa7134: card=18 -> BMK MPEX No Tuner
[12465.028592] saa7134: card=19 -> Compro VideoMate TV 185b:c100
[12465.028600] saa7134: card=20 -> Matrox CronosPlus 102b:48d0
[12465.028608] saa7134: card=21 -> 10MOONS PCI TV CAPTURE CARD 1131:2001
[12465.028617] saa7134: card=22 -> AverMedia M156 / Medion 2819 1461:a70b
[12465.028625] saa7134: card=23 -> BMK MPEX Tuner
[12465.028632] saa7134: card=24 -> KNC One TV-Station DVR 1894:a006
[12465.028640] saa7134: card=25 -> ASUS TV-FM 7133 1043:4843
[12465.028648] saa7134: card=26 -> Pinnacle PCTV Stereo (saa7134) 11bd:002b
[12465.028657] saa7134: card=27 -> Manli MuchTV M-TV002
[12465.028663] saa7134: card=28 -> Manli MuchTV M-TV001
[12465.028670] saa7134: card=29 -> Nagase Sangyo TransGear 3000TV 1461:050c
[12465.028679] saa7134: card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[12465.028687] saa7134: card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card 1019:4cb5
[12465.028695] saa7134: card=32 -> AVACS SmartTV
[12465.028702] saa7134: card=33 -> AVerMedia DVD EZMaker 1461:10ff
[12465.028710] saa7134: card=34 -> Noval Prime TV 7133
[12465.028717] saa7134: card=35 -> AverMedia AverTV Studio 305 1461:2115
[12465.028725] saa7134: card=36 -> UPMOST PURPLE TV 12ab:0800
[12465.028734] saa7134: card=37 -> Items MuchTV Plus / IT-005
[12465.028740] saa7134: card=38 -> Terratec Cinergy 200 TV 153b:1152
[12465.028749] saa7134: card=39 -> LifeView FlyTV Platinum Mini 5168:0212 4e42:0212 5169:1502
[12465.028760] saa7134: card=40 -> Compro VideoMate TV PVR/FM 185b:c100
[12465.028768] saa7134: card=41 -> Compro VideoMate TV Gold+ 185b:c100
[12465.028776] saa7134: card=42 -> Sabrent SBT-TVFM (saa7130)
[12465.028783] saa7134: card=43 -> :Zolid Xpert TV7134
[12465.028790] saa7134: card=44 -> Empire PCI TV-Radio LE
[12465.028796] saa7134: card=45 -> Avermedia AVerTV Studio 307 1461:9715
[12465.028805] saa7134: card=46 -> AVerMedia Cardbus TV/Radio (E500) 1461:d6ee
[12465.028813] saa7134: card=47 -> Terratec Cinergy 400 mobile 153b:1162
[12465.028821] saa7134: card=48 -> Terratec Cinergy 600 TV MK3 153b:1158
[12465.028830] saa7134: card=49 -> Compro VideoMate Gold+ Pal 185b:c200
[12465.028838] saa7134: card=50 -> Pinnacle PCTV 300i DVB-T + PAL 11bd:002d
[12465.028847] saa7134: card=51 -> ProVideo PV952 1540:9524
[12465.028855] saa7134: card=52 -> AverMedia AverTV/305 1461:2108
[12465.028863] saa7134: card=53 -> ASUS TV-FM 7135 1043:4845
[12465.028871] saa7134: card=54 -> LifeView FlyTV Platinum FM / Gold 5168:0214 5168:5214 1489:0214 5168:0304
[12465.028884] saa7134: card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[12465.028894] saa7134: card=56 -> Avermedia AVerTV 307 1461:a70a
[12465.028903] saa7134: card=57 -> Avermedia AVerTV GO 007 FM 1461:f31f
[12465.028911] saa7134: card=58 -> ADS Tech Instant TV (saa7135) 1421:0350 1421:0351 1421:0370 1421:1370
[12465.028924] saa7134: card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[12465.028931] saa7134: card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[12465.028942] saa7134: card=61 -> Philips TOUGH DVB-T reference design 1131:2004
[12465.028951] saa7134: card=62 -> Compro VideoMate TV Gold+II
[12465.028958] saa7134: card=63 -> Kworld Xpert TV PVR7134
[12465.028964] saa7134: card=64 -> FlyTV mini Asus Digimatrix 1043:0210
[12465.028973] saa7134: card=65 -> V-Stream Studio TV Terminator
[12465.028980] saa7134: card=66 -> Yuan TUN-900 (saa7135)
[12465.028986] saa7134: card=67 -> Beholder BeholdTV 409 FM 0000:4091
[12465.028995] saa7134: card=68 -> GoTView 7135 PCI 5456:7135
[12465.029003] saa7134: card=69 -> Philips EUROPA V3 reference design 1131:2004
[12465.029011] saa7134: card=70 -> Compro Videomate DVB-T300 185b:c900
[12465.029020] saa7134: card=71 -> Compro Videomate DVB-T200 185b:c901
[12465.029028] saa7134: card=72 -> RTD Embedded Technologies VFG7350 1435:7350
[12465.029036] saa7134: card=73 -> RTD Embedded Technologies VFG7330 1435:7330
[12465.029045] saa7134: card=74 -> LifeView FlyTV Platinum Mini2 14c0:1212
[12465.029053] saa7134: card=75 -> AVerMedia AVerTVHD MCE A180 1461:1044
[12465.029062] saa7134: card=76 -> SKNet MonsterTV Mobile 1131:4ee9
[12465.029070] saa7134: card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133) 11bd:002e
[12465.029078] saa7134: card=78 -> ASUSTeK P7131 Dual 1043:4862
[12465.029087] saa7134: card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[12465.029094] saa7134: card=80 -> ASUS Digimatrix TV 1043:0210
[12465.029102] saa7134: card=81 -> Philips Tiger reference design 1131:2018
[12465.029110] saa7134: card=82 -> MSI TV@Anywhere plus 1462:6231 1462:8624
[12465.029120] saa7134: card=83 -> Terratec Cinergy 250 PCI TV 153b:1160
[12465.029128] saa7134: card=84 -> LifeView FlyDVB Trio 5168:0319
[12465.029137] saa7134: card=85 -> AverTV DVB-T 777 1461:2c05 1461:2c05
[12465.029147] saa7134: card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[12465.029156] saa7134: card=87 -> ADS Instant TV Duo Cardbus PTV331 0331:1421
[12465.029165] saa7134: card=88 -> Tevion/KWorld DVB-T 220RF 17de:7201
[12465.029173] saa7134: card=89 -> ELSA EX-VISION 700TV 1048:226c
[12465.029182] saa7134: card=90 -> Kworld ATSC110/115 17de:7350 17de:7352
[12465.029191] saa7134: card=91 -> AVerMedia A169 B 1461:7360
[12465.029200] saa7134: card=92 -> AVerMedia A169 B1 1461:6360
[12465.029208] saa7134: card=93 -> Medion 7134 Bridge #2 16be:0005
[12465.029216] saa7134: card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV 5168:3306 5168:3502 5168:3307 4e42:3502
[12465.029229] saa7134: card=95 -> LifeView FlyVIDEO3000 (NTSC) 5169:0138
[12465.029238] saa7134: card=96 -> Medion Md8800 Quadro 16be:0007 16be:0008 16be:000d
[12465.029249] saa7134: card=97 -> LifeView FlyDVB-S /Acorp TV134DS 5168:0300 4e42:0300
[12465.029259] saa7134: card=98 -> Proteus Pro 2309 0919:2003
[12465.029267] saa7134: card=99 -> AVerMedia TV Hybrid A16AR 1461:2c00
[12465.029276] saa7134: card=100 -> Asus Europa2 OEM 1043:4860
[12465.029284] saa7134: card=101 -> Pinnacle PCTV 310i 11bd:002f
[12465.029293] saa7134: card=102 -> Avermedia AVerTV Studio 507 1461:9715
[12465.029301] saa7134: card=103 -> Compro Videomate DVB-T200A
[12465.029308] saa7134: card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid 0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[12465.029324] saa7134: card=105 -> Terratec Cinergy HT PCMCIA 153b:1172
[12465.029332] saa7134: card=106 -> Encore ENLTV 1131:2342 1131:2341 3016:2344
[12465.029344] saa7134: card=107 -> Encore ENLTV-FM 1131:230f
[12465.029352] saa7134: card=108 -> Terratec Cinergy HT PCI 153b:1175
[12465.029360] saa7134: card=109 -> Philips Tiger - S Reference design
[12465.029367] saa7134: card=110 -> Avermedia M102 1461:f31e
[12465.029375] saa7134: card=111 -> ASUS P7131 4871 1043:4871
[12465.029384] saa7134: card=112 -> ASUSTeK P7131 Hybrid 1043:4876
[12465.029392] saa7134: card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card 1019:4cb6
[12465.029401] saa7134: card=114 -> KWorld DVB-T 210 17de:7250
[12465.029409] saa7134: card=115 -> Sabrent PCMCIA TV-PCB05 0919:2003
[12465.029418] saa7134: card=116 -> 10MOONS TM300 TV Card 1131:2304
[12465.029426] saa7134: card=117 -> Avermedia Super 007 1461:f01d
[12465.029435] saa7134: card=118 -> Beholder BeholdTV 401 0000:4016
[12465.029443] saa7134: card=119 -> Beholder BeholdTV 403 0000:4036
[12465.029451] saa7134: card=120 -> Beholder BeholdTV 403 FM 0000:4037
[12465.029459] saa7134: card=121 -> Beholder BeholdTV 405 0000:4050
[12465.029468] saa7134: card=122 -> Beholder BeholdTV 405 FM 0000:4051
[12465.029476] saa7134: card=123 -> Beholder BeholdTV 407 0000:4070
[12465.029484] saa7134: card=124 -> Beholder BeholdTV 407 FM 0000:4071
[12465.029493] saa7134: card=125 -> Beholder BeholdTV 409 0000:4090
[12465.029501] saa7134: card=126 -> Beholder BeholdTV 505 FM 5ace:5050
[12465.029510] saa7134: card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509 5ace:5070 5ace:5090
[12465.029520] saa7134: card=128 -> Beholder BeholdTV Columbus TVFM 0000:5201
[12465.029528] saa7134: card=129 -> Beholder BeholdTV 607 FM 5ace:6070
[12465.029537] saa7134: card=130 -> Beholder BeholdTV M6 5ace:6190
[12465.029545] saa7134: card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI 1822:0022
[12465.029554] saa7134: card=132 -> Genius TVGO AM11MCE
[12465.029560] saa7134: card=133 -> NXP Snake DVB-S reference design
[12465.029567] saa7134: card=134 -> Medion/Creatix CTX953 Hybrid 16be:0010
[12465.029576] saa7134: card=135 -> MSI TV@nywhere A/D v1.1 1462:8625
[12465.029584] saa7134: card=136 -> AVerMedia Cardbus TV/Radio (E506R) 1461:f436
[12465.029592] saa7134: card=137 -> AVerMedia Hybrid TV/Radio (A16D) 1461:f936
[12465.029601] saa7134: card=138 -> Avermedia M115 1461:a836
[12465.029609] saa7134: card=139 -> Compro VideoMate T750 185b:c900
[12465.029617] saa7134: card=140 -> Avermedia DVB-S Pro A700 1461:a7a1
[12465.029626] saa7134: card=141 -> Avermedia DVB-S Hybrid+FM A700 1461:a7a2
[12465.029634] saa7134: card=142 -> Beholder BeholdTV H6 5ace:6290
[12465.029642] saa7134: card=143 -> Beholder BeholdTV M63 5ace:6191
[12465.029651] saa7134: card=144 -> Beholder BeholdTV M6 Extra 5ace:6193
[12465.029659] saa7134: card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103 1461:f636 1461:f736
[12465.029669] saa7134: card=146 -> ASUSTeK P7131 Analog
[12465.029676] saa7134: card=147 -> Asus Tiger 3in1 1043:4878
[12465.029684] saa7134: card=148 -> Encore ENLTV-FM v5.3 1a7f:2008
[12465.029693] saa7134: card=149 -> Avermedia PCI pure analog (M135A) 1461:f11d
[12465.029701] saa7134: card=150 -> Zogis Real Angel 220
[12465.029708] saa7134: card=151 -> ADS Tech Instant HDTV 1421:0380
[12465.029716] saa7134: card=152 -> Asus Tiger Rev:1.00 1043:4857
[12465.029725] saa7134: card=153 -> Kworld Plus TV Analog Lite PCI 17de:7128
[12465.029733] saa7134: card=154 -> Avermedia AVerTV GO 007 FM Plus 1461:f31d
[12465.029742] saa7134: card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid 0070:6706 0070:6708
[12465.029752] saa7134: card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid 0070:6707 0070:6709 0070:670a
[12465.029763] saa7134: card=157 -> Avermedia AVerTV Studio 507UA 1461:a11b
[12465.029772] saa7134: card=158 -> AVerMedia Cardbus TV/Radio (E501R) 1461:b7e9
[12465.029780] saa7134: card=159 -> Beholder BeholdTV 505 RDS 0000:505b
[12465.029789] saa7134: card=160 -> Beholder BeholdTV 507 RDS 0000:5071
[12465.029797] saa7134: card=161 -> Beholder BeholdTV 507 RDS 0000:507b
[12465.029806] saa7134: card=162 -> Beholder BeholdTV 607 FM 5ace:6071
[12465.029815] saa7134: card=163 -> Beholder BeholdTV 609 FM 5ace:6090
[12465.029823] saa7134: card=164 -> Beholder BeholdTV 609 FM 5ace:6091
[12465.029832] saa7134: card=165 -> Beholder BeholdTV 607 RDS 5ace:6072
[12465.029840] saa7134: card=166 -> Beholder BeholdTV 607 RDS 5ace:6073
[12465.029849] saa7134: card=167 -> Beholder BeholdTV 609 RDS 5ace:6092
[12465.029857] saa7134: card=168 -> Beholder BeholdTV 609 RDS 5ace:6093
[12465.029866] saa7134: card=169 -> Compro VideoMate S350/S300 185b:c900
[12465.029874] saa7134: card=170 -> AverMedia AverTV Studio 505 1461:a115
[12465.029883] saa7134: card=171 -> Beholder BeholdTV X7 5ace:7595
[12465.029892] saa7134: card=172 -> RoverMedia TV Link Pro FM 19d1:0138
[12465.029900] saa7134: card=173 -> Zolid Hybrid TV Tuner PCI 1131:2004
[12465.029909] saa7134: card=174 -> Asus Europa Hybrid OEM 1043:4847
[12465.029917] saa7134: card=175 -> Leadtek Winfast DTV1000S 107d:6655
[12465.029926] saa7134: card=176 -> Beholder BeholdTV 505 RDS 0000:5051
[12465.029934] saa7134: card=177 -> Hawell HW-404M7
[12465.029941] saa7134: card=178 -> Beholder BeholdTV H7
[12465.029948] saa7134: card=179 -> Beholder BeholdTV A7
[12465.029955] saa7134: card=180 -> Avermedia PCI M733A 1461:4155 1461:4255
[12465.029967] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[12465.030033] saa7130[0]: can't get MMIO memory @ 0x0
[12465.030051] saa7134: probe of 0000:01:07.0 failed with error -16
[12465.053892] saa7134 ALSA driver for DMA sound loaded
[12465.053900] saa7134 ALSA: no saa7134 cards found
 **tvtime-scanner**

  Leyendo la configuración de /etc/tvtime/tvtime.xml
Leyendo la configuración de /home/ricardo/.tvtime/tvtime.xml
Escaneando usando la norma de TV NTSC.
/home/ricardo/.tvtime/stationlist.xml: No existing NTSC station list "Custom".
videoinput: Cannot open capture device /dev/video0: No existe el dispositivo o la dirección
 **ls /dev/**

  autofs           disk      fd0u1743  hpet   lp0                 pktcdvd  ram14   root  sg2       tty11  tty22  tty33  tty44  tty55  tty9     vcs2   vcsa6
block            dvd       fd0u1760  input  mapper              port     ram15   rtc   shm       tty12  tty23  tty34  tty45  tty56  ttyS0    vcs3   vcsa7
bsg              dvdrw     fd0u1840  kmsg   mcelog              ppp      ram2    rtc0  snapshot  tty13  tty24  tty35  tty46  tty57  ttyS1    vcs4   vga_arbiter
btrfs-control    ecryptfs  fd0u1920  log    mem                 psaux    ram3    scd0  snd       tty14  tty25  tty36  tty47  tty58  ttyS2    vcs5   zero
bus              fd        fd0u360   loop0  net                 ptmx     ram4    sda   sr0       tty15  tty26  tty37  tty48  tty59  ttyS3    vcs6
c    drom            fd0       fd0u720   loop1  network_latency     pts      ram5    sda1  stderr    tty16  tty27  tty38  tty49  tty6   uinput   vcs7
cdrw             fd0u1040  fd0u800   loop2  network_throughput  ram0     ram6    sdb   stdin     tty17  tty28  tty39  tty5   tty60  urandom  vcsa
char             fd0u1120  fd0u820   loop3  null                ram1     ram7    sdb1  stdout    tty18  tty29  tty4   tty50  tty61  usbmon0  vcsa1
console          fd0u1440  fd0u830   loop4  nvidia0             ram10    ram8    sdb2  tty       tty19  tty3   tty40  tty51  tty62  usbmon1  vcsa2
core             fd0u1600  full      loop5  nvidiactl           ram11    ram9    sdb5  tty0      tty2   tty30  tty41  tty52  tty63  usbmon2  vcsa3
cpu              fd0u1680  fuse      loop6  oldmem              ram12    random  sg0   tty1      tty20  tty31  tty42  tty53  tty7   vcs      vcsa4
cpu_dma_latency  fd0u1722  hidraw0   loop7  parport0            ram13    rfkill  sg1   tty10     tty21  tty32  tty43  tty54  tty8   vcs1     vcsa5
 I followed the steps down here [http://askubuntu.com/questions/19849/how-do-you-setup-the-driver-for-a-philips-based-tv-capture-card](http://askubuntu.com/questions/19849/how-do-you-setup-the-driver-for-a-philips-based-tv-capture-card) and still nothing i think is 42 my video card is this: [http://www.geeks.com/details.asp?invtid=TV-PCIRC&cat=VID](http://www.geeks.com/details.asp?invtid=TV-PCIRC&cat=VID)
  And when i start tvtime it closes automatically.

---

### Post by laceration on 2011-01-04
I must have answered a question like this about 10 times on these forums.

**[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)**
**[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)**
**[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)**

This is a wiki created by the people who do the actual kernel programming for TV capture devices and it is very comprehensive with clear instructions.
Suggested use:
Find your device type -- DVB-C, DVB-T, ATSC, etc., different regions of the world have different types, then find your device.  Then you find out if your device is supported -- most are -- and how to set it up.

---


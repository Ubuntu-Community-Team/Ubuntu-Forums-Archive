---
title: "pixelview play tv pro 3 tv card not working"
date: 2008-05-11
forum: Multimedia Software
---

### Post by squallwc on 2008-05-11
> **update:**
Got it working with card=42 tuner=38. Enjoy.

Pixelview play tv pro 3
I have researched a little and get myself a pixelview card but apparently it has different chipset than ver.2. This is a clean install of ubuntu with nvidia driver installed. My TV card model is not working out of the box and not one of the listed tv cards in v4l tv card list.

1) Anyone with the same card can show me the way?
2) What to do when my tv card model and not even the brand is on the list?
3) Am I suppose to try out one by one through out the whole list of 100+ tv card options and then tvtime-scanner to see whether it is working? And from what I read, tv card and tunner has different combinations as well. OMG. :(
4) How do I know when I have chosen the correct card and tuner?

Is there any alternative way to do it? Sabotage the tv signal in the living room for a long time is not a good option.

I have checked the latest [SAA7134 cardlist]("http://linuxtv.org/hg/v4l-dvb/file/tip/linux/Documentation/video4linux/CARDLIST.saa7134") from v4l site. My tv card is not there.

**lspci -v**
```

02:05.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors Unknown device 0000
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at ee011000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

```

**xawtv -hwscan**
```
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UNKNOWN/GENERIC
    flags: overlay capture  
```

original **dmesg**
```
[   38.003997] saa7130/34: v4l2 driver version 0.2.14 loaded
[   38.004110] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[   38.004120] saa7130[0]: found at 0000:02:05.0, rev: 1, irq: 18, latency: 32, mmio: 0xee011000
[   38.004126] saa7134: <rant>
[   38.004127] saa7134:  Congratulations!  Your TV card vendor saved a few
[   38.004129] saa7134:  cents for a eeprom, thus your pci board has no
[   38.004130] saa7134:  subsystem ID and I can't identify it automatically
[   38.004131] saa7134: </rant>
[   38.004132] saa7134: I feel better now.  Ok, here are the good news:
[   38.004133] saa7134: You can use the card=<nr> insmod option to specify
[   38.004134] saa7134: which board do you have.  The list:
[   38.004138] saa7134:   card=0 -> UNKNOWN/GENERIC
[   38.004141] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   38.004146] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   38.004151] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   38.004156] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   38.004160] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   38.004164] saa7134:   card=6 -> Tevion MD 9717
[   38.004167] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   38.004172] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   38.004176] saa7134:   card=9 -> Medion 5044
[   38.004179] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
[   38.004181] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   38.004185] saa7134:   card=12 -> Medion 7134                              16be:0003
[   38.004189] saa7134:   card=13 -> Typhoon TV+Radio 90031
[   38.004192] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   38.004196] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   38.004200] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   38.004205] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   38.004209] saa7134:   card=18 -> BMK MPEX No Tuner
[   38.004212] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   38.004216] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   38.004220] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   38.004224] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   38.004228] saa7134:   card=23 -> BMK MPEX Tuner
[   38.004231] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   38.004235] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   38.004239] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   38.004242] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM
[   38.004245] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401
[   38.004248] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   38.004252] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   38.004256] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   38.004260] saa7134:   card=32 -> AVACS SmartTV
[   38.004262] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   38.004266] saa7134:   card=34 -> Noval Prime TV 7133
[   38.004269] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   38.004273] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   38.004277] saa7134:   card=37 -> Items MuchTV Plus / IT-005
[   38.004280] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   38.004284] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   38.004288] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   38.004292] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   38.004296] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)
[   38.004299] saa7134:   card=43 -> :Zolid Xpert TV7134
[   38.004302] saa7134:   card=44 -> Empire PCI TV-Radio LE
[   38.004305] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   38.004309] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   38.004313] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   38.004317] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   38.004321] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   38.004324] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   38.004328] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   38.004332] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   38.004336] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   38.004340] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   38.004347] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   38.004351] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   38.004355] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   38.004359] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   38.004366] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[   38.004368] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   38.004374] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   38.004378] saa7134:   card=62 -> Compro VideoMate TV Gold+II
[   38.004381] saa7134:   card=63 -> Kworld Xpert TV PVR7134
[   38.004384] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   38.004388] saa7134:   card=65 -> V-Stream Studio TV Terminator
[   38.004390] saa7134:   card=66 -> Yuan TUN-900 (saa7135)
[   38.004393] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   38.004397] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   38.004401] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   38.004405] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   38.004409] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   38.004413] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   38.004417] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   38.004421] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   38.004425] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   38.004429] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   38.004432] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   38.004436] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   38.004441] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   38.004444] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   38.004448] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   38.004452] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   38.004456] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   38.004459] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   38.004463] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   38.004468] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   38.004473] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   38.004477] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   38.004481] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   38.004485] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   38.004489] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   38.004493] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   38.004497] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   38.004501] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 4e42:3502
[   38.004507] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   38.004511] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   38.004515] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   38.004520] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   38.004524] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   38.004528] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   38.004532] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   38.004536] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   38.004539] saa7134:   card=103 -> Compro Videomate DVB-T200A
[   38.004542] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   38.004546] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   38.004550] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   38.004556] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   38.004560] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   38.004563] saa7134:   card=109 -> Philips Tiger - S Reference design
[   38.004566] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   38.004570] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   38.004574] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   38.004578] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   38.004582] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   38.004586] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   38.004590] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304

[   38.004594] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   38.004598] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   38.004615] saa7130[0]: board init: gpio is 60c000
[   38.108059] saa7130[0]: Huh, no eeprom present (err=-5)?
[   38.108110] saa7130[0]: registered device video0 [v4l2]
[   38.108132] saa7130[0]: registered device vbi0
[   38.115370] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.115773] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   38.140363] saa7134 ALSA driver for DMA sound loaded
[   38.140402] saa7130[0]/alsa: saa7130[0] at 0xee011000 irq 18 registered as card -2
[   39.622730] Bluetooth: Core ver 2.11
[   39.641607] NET: Registered protocol family 31
[   39.641612] Bluetooth: HCI device and connection manager initialized
[   39.641617] Bluetooth: HCI socket layer initialized
[   39.667865] Bluetooth: HCI USB driver ver 2.9
[   39.669864] saa7130[0]/irq[10,-69757]: r=0x20 s=0x00 PE
[   39.669870] saa7130[0]/irq: looping -- clearing PE (parity error!) enable bit
```

Following the various guides online, I tried to rmmod and modprobe saa7134 with i2c scan. Seems like the tv card is still not detected but tuner get detected.
**rmmod saa7134-alsa**
**rmmod saa7134**
**modprobe saa7134 i2c_scan=1**
**dmesg**
```
[ 2880.703519] saa7134 ALSA driver for DMA sound unloaded
[ 2905.878361] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 2905.878437] saa7130[0]: found at 0000:02:05.0, rev: 1, irq: 18, latency: 32, mmio: 0xee011000
[ 2905.878445] saa7134: <rant>
[ 2905.878446] saa7134:  Congratulations!  Your TV card vendor saved a few
[ 2905.878448] saa7134:  cents for a eeprom, thus your pci board has no
[ 2905.878449] saa7134:  subsystem ID and I can't identify it automatically
[ 2905.878451] saa7134: </rant>
[ 2905.878451] saa7134: I feel better now.  Ok, here are the good news:
[ 2905.878453] saa7134: You can use the card=<nr> insmod option to specify
[ 2905.878454] saa7134: which board do you have.  The list:
[ 2905.878458] saa7134:   card=0 -> UNKNOWN/GENERIC
[ 2905.878462] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[ 2905.878467] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[ 2905.878472] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[ 2905.878477] saa7134:   card=4 -> EMPRESS                                  1131:6752
[ 2905.878481] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[ 2905.878485] saa7134:   card=6 -> Tevion MD 9717
[ 2905.878489] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[ 2905.878494] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[ 2905.878498] saa7134:   card=9 -> Medion 5044
[ 2905.878501] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
[ 2905.878504] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[ 2905.878508] saa7134:   card=12 -> Medion 7134                              16be:0003
[ 2905.878512] saa7134:   card=13 -> Typhoon TV+Radio 90031
[ 2905.878515] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[ 2905.878520] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[ 2905.878524] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[ 2905.878530] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[ 2905.878534] saa7134:   card=18 -> BMK MPEX No Tuner
[ 2905.878537] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[ 2905.878541] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[ 2905.878546] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[ 2905.878550] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[ 2905.878554] saa7134:   card=23 -> BMK MPEX Tuner
[ 2905.878557] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[ 2905.878587] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[ 2905.878592] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[ 2905.878596] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM
[ 2905.878599] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401
[ 2905.878602] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[ 2905.878606] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[ 2905.878610] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[ 2905.878614] saa7134:   card=32 -> AVACS SmartTV
[ 2905.878617] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[ 2905.878620] saa7134:   card=34 -> Noval Prime TV 7133
[ 2905.878624] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[ 2905.878628] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[ 2905.878631] saa7134:   card=37 -> Items MuchTV Plus / IT-005
[ 2905.878634] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[ 2905.878638] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[ 2905.878643] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[ 2905.878647] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[ 2905.878651] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)
[ 2905.878654] saa7134:   card=43 -> :Zolid Xpert TV7134
[ 2905.878656] saa7134:   card=44 -> Empire PCI TV-Radio LE
[ 2905.878659] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[ 2905.878663] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[ 2905.878667] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[ 2905.878671] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[ 2905.878675] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[ 2905.878679] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[ 2905.878683] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[ 2905.878687] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[ 2905.878690] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[ 2905.878694] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[ 2905.878701] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[ 2905.878705] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[ 2905.878709] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[ 2905.878713] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[ 2905.878719] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[ 2905.878722] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[ 2905.878728] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[ 2905.878732] saa7134:   card=62 -> Compro VideoMate TV Gold+II
[ 2905.878735] saa7134:   card=63 -> Kworld Xpert TV PVR7134
[ 2905.878738] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[ 2905.878742] saa7134:   card=65 -> V-Stream Studio TV Terminator
[ 2905.878745] saa7134:   card=66 -> Yuan TUN-900 (saa7135)
[ 2905.878747] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[ 2905.878751] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[ 2905.878755] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[ 2905.878759] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[ 2905.878763] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[ 2905.878767] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[ 2905.878771] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[ 2905.878775] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[ 2905.878779] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[ 2905.878782] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[ 2905.878786] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[ 2905.878790] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[ 2905.878795] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[ 2905.878798] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[ 2905.878802] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[ 2905.878805] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[ 2905.878809] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[ 2905.878813] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[ 2905.878817] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[ 2905.878822] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[ 2905.878827] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[ 2905.878830] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[ 2905.878834] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[ 2905.878838] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[ 2905.878843] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[ 2905.878847] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[ 2905.878851] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[ 2905.878854] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 4e42:3502
[ 2905.878860] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[ 2905.878864] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[ 2905.878869] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[ 2905.878873] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[ 2905.878877] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[ 2905.878881] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[ 2905.878885] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[ 2905.878889] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[ 2905.878893] saa7134:   card=103 -> Compro Videomate DVB-T200A
[ 2905.878896] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[ 2905.878900] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[ 2905.878903] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[ 2905.878909] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[ 2905.878913] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[ 2905.878917] saa7134:   card=109 -> Philips Tiger - S Reference design
[ 2905.878920] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[ 2905.878924] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[ 2905.878927] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[ 2905.878931] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[ 2905.878935] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[ 2905.878939] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[ 2905.878943] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[ 2905.878947] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[ 2905.878951] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[ 2905.878971] saa7130[0]: board init: gpio is 60c000
[ 2905.981156] saa7130[0]: Huh, no eeprom present (err=-5)?
[ 2906.005386] saa7130[0]: i2c scan: found device @ 0xc0  [tuner (analog)]
[ 2906.011727] saa7130[0]: registered device video0 [v4l2]
[ 2906.011755] saa7130[0]: registered device vbi0
[ 2906.020007] saa7130[0]/irq[10,647280]: r=0x20 s=0x00 PE
[ 2906.020013] saa7130[0]/irq: looping -- clearing PE (parity error!) enable bit
[ 2906.063928] saa7134 ALSA driver for DMA sound loaded
[ 2906.063973] saa7130[0]/alsa: saa7130[0] at 0xee011000 irq 18 registered as card -2

```

Then I searched and found a thread talking about pixelview pcmia card with saa7134 chip. Followed the forum put card=79 tuner=2. tvtime-scanner scanning channel for a long time. No signal found after it scans through half of the spectrum. hmm..

---

### Post by xc3RnbFO8P on 2008-05-11
Maybe this will help:
[http://www.linuxtv.org/v4lwiki/index.php/Pixelview_PlayTV_Pro_Ultra]("http://www.linuxtv.org/v4lwiki/index.php/Pixelview_PlayTV_Pro_Ultra")

---

### Post by squallwc on 2008-05-11
> **Ringi said:**
> Maybe this will help:
[http://www.linuxtv.org/v4lwiki/index.php/Pixelview_PlayTV_Pro_Ultra]("http://www.linuxtv.org/v4lwiki/index.php/Pixelview_PlayTV_Pro_Ultra")
Different chipset. Mine is SAA7130 not cx88xx. according to lspci.

---

### Post by xc3RnbFO8P on 2008-05-12
Then look at this:
> UPDATE Dec 2007
Hmm this guide seems quite old&#8230;I&#8217;m using ubuntu now
For ubuntu user the provided kernel already support cx88 based card with radio FM.
You just need to add the following module options to /etc/modprobe.d/options
options cx8800 video_nr=0 radio_nr=0
options cx88xx card=3 tuner=5
and then reload the module

[http://anmsid.blogsome.com/2005/03/18/pixelview-play-tv-pro-cx88-quick-installation/]("http://anmsid.blogsome.com/2005/03/18/pixelview-play-tv-pro-cx88-quick-installation/")

---

### Post by squallwc on 2008-05-25
Update to this problem.

***modprobe saa7134 card=79 i2c-scan=1***
I connect a composite video in signal and able to view the video source.

***tvtime-scanner***
With the same setting. Plug in a tv antenna. Channel scanning with tvtime seems to take forever. Could be weak signal problem.

Will try with another tv-in later.

---

### Post by squallwc on 2008-05-31
Update again:
Finally got it to work.

modprobe saa7134 card=79 tuner=43

tvtime-scanner pick up some tv channels. Able to watch tv now. But no sound at all.

I connect the audio out from my tv card into the line in on my sound card. Been playing with alsamixer for a while. Still no sound at all.

Yea. I'm in the audio usergroup. And line in is not mute.

Maybe it is due to incorrect card/tuner? But the tv video quality I get is very clear.

This is becoming a daunting job. Maybe go and get another tv card will do. =.=

---

### Post by gibz85 on 2008-06-27
here this what worked for me...........

I switched the card to card=42 tuner to tuner=38 added this to kernel module and restarted the linux box(OPensue11) Open kdetv worked like a charm...

playTv pro3... Gets sound and whole channel... enjoy.......

---

### Post by squallwc on 2008-07-13
card=42 tuner=38
It works.

Using line-in as audio-input.
For mythtv, mute the line-in. Recording and live tv view working fine.

Update for the other tv card owners. :)

---

### Post by benrod on 2008-07-23
Hi, I'm newbie with Ubuntu Linux. Can you explain step by step how to configure that tv card?
Anyhoo, My tv card also Pixelview Play Tv Pro 3.

---

### Post by gibz85 on 2008-07-25
Are you usinig ubuntu....If yess. it is little harder than other... Well we have to add the card and tuner in to kernele module parameter,,,,

If you have configure your card before user rmmod to remove the parameter

and use

modprobe saa7134 card=42 tuner=38 as su user

reboot the machine it should work... 

SOrry this mighnt not help you as expanation is not enough(suse has spoiled me)

---

### Post by StarryKnight on 2009-04-10
> **squallwc said:**
> card=42 tuner=38
It works.



Had to bump this thread, as i have the same card. And i'm a n00b to linux, can someone please tell me where do i have to enter the above code (the terminal??)? and what all else i have to do to get it running? it'll be a big favor, thanks :)

---


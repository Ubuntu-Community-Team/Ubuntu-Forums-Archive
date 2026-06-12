---
title: "Need Help: Setting up TV Tuner card for Laptop - saa7134"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by grnqrtr on 2007-01-17
I need help setting up my TV Tuner card for my laptop.  I have done many searches in google and in the forum and have followed some tutorials and still can't get my card to work.

It is a Norwood Micro Notebook Cardbus TV Tuner Adapter that I bought at CompUSA.
I am using 6.10 Edgy Eft and I have been trying the card in tvtime, xawtv and zapping.

If I use the command *lspci*, it shows up as:
```
07:00.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
```

If I do *modprobe saa7134 dmesg*, I get:
```
[17208393.372000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 177, latency: 0, mmio: 0x52000000
[17208393.372000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[17208393.372000] saa7134: <rant>
[17208393.372000] saa7134:  Congratulations!  Your TV card vendor saved a few
[17208393.372000] saa7134:  cents for a eeprom, thus your pci board has no
[17208393.372000] saa7134:  subsystem ID and I can't identify it automatically
[17208393.372000] saa7134: </rant>
[17208393.372000] saa7134: I feel better now.  Ok, here are the good news:
[17208393.372000] saa7134: You can use the card=<nr> insmod option to specify
[17208393.372000] saa7134: which board do you have.  The list:
[17208393.372000] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[17208393.372000] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[17208393.372000] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[17208393.372000] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[17208393.372000] saa7134:   card=4 -> EMPRESS                                  1131:6752
[17208393.372000] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[17208393.372000] saa7134:   card=6 -> Tevion MD 9717                          
[17208393.372000] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[17208393.372000] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[17208393.372000] saa7134:   card=9 -> Medion 5044                             
[17208393.372000] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[17208393.372000] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[17208393.372000] saa7134:   card=12 -> Medion 7134                              16be:0003
[17208393.372000] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[17208393.372000] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[17208393.372000] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[17208393.372000] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[17208393.372000] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[17208393.372000] saa7134:   card=18 -> BMK MPEX No Tuner                       
[17208393.372000] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[17208393.372000] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[17208393.372000] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[17208393.372000] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[17208393.372000] saa7134:   card=23 -> BMK MPEX Tuner                          
[17208393.372000] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[17208393.372000] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[17208393.372000] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[17208393.372000] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[17208393.372000] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[17208393.372000] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[17208393.372000] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[17208393.372000] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[17208393.372000] saa7134:   card=32 -> AVACS SmartTV                           
[17208393.372000] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[17208393.372000] saa7134:   card=34 -> Noval Prime TV 7133                     
[17208393.372000] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[17208393.372000] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[17208393.372000] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[17208393.372000] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[17208393.372000] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[17208393.372000] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[17208393.372000] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[17208393.372000] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[17208393.372000] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[17208393.372000] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[17208393.372000] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[17208393.372000] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[17208393.372000] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[17208393.372000] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[17208393.372000] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[17208393.372000] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[17208393.372000] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[17208393.372000] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[17208393.372000] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[17208393.372000] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 1489:0214 5168:0304
[17208393.372000] saa7134:   card=55 -> LifeView FlyDVB-T DUO                    5168:0306
[17208393.372000] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[17208393.372000] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[17208393.372000] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[17208393.372000] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[17208393.372000] saa7134:   card=60 -> LifeView/Typhoon FlyDVB-T Duo Cardbus    5168:0502 4e42:0502
[17208393.372000] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[17208393.372000] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[17208393.372000] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[17208393.372000] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[17208393.372000] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[17208393.372000] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[17208393.372000] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[17208393.372000] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[17208393.372000] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[17208393.372000] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[17208393.372000] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[17208393.372000] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[17208393.372000] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[17208393.372000] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[17208393.372000] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[17208393.372000] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[17208393.372000] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[17208393.372000] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[17208393.372000] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[17208393.372000] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[17208393.372000] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[17208393.372000] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[17208393.372000] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[17208393.372000] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[17208393.372000] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05
[17208393.372000] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[17208393.372000] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[17208393.372000] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[17208393.372000] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[17208393.372000] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[17208393.372000] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[17208393.372000] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[17208393.372000] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[17208393.372000] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[17208393.372000] saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[17208393.372000] saa7134[0]: board init: gpio is e2c0c0
[17208393.476000] saa7134[0]: Huh, no eeprom present (err=-5)?
[17208393.476000] saa7134[0]: registered device video0 [v4l2]
[17208393.476000] saa7134[0]: registered device vbi0
[17208393.476000] saa7134[0]/alsa: saa7134[0] at 0x52000000 irq 177 registered as card -1

```

From what I've found while searching it seems that an saa7134 card is supposed to be pretty easy to set up, but I have been having a lot of trouble.  All I care about getting setup is composite video, I just want to be able to play my xbox with the card.

I am a noob, but I tried to do a lot of searching before I asked for help because I know it is annoying when someone asks for help and if they had took a couple minutes to search they would have found their answer.

Any help would be greatly appreciated.  Thanks.

---

### Post by phossal on 2007-01-18
Check out the site for TV Time. If you read the information they have available, you might get an idea on which driver set your card is using. I had similar troubles with my own card (and most people do). While the common cards are often very well supported, they're commonly not *recognized* well. Many times the solution is as simple as finding the correct tuner/card numbers and setting them. 

Check out my [trouble here]("http://ubuntuforums.org/showthread.php?t=332261"), [my solution (pay attention to the note)]("http://ubuntuforums.org/showthread.php?t=338182"), and then head to TV Time. Good luck.

---


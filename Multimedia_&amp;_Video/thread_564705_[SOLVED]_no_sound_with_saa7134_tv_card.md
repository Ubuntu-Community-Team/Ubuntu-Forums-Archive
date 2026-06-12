---
title: "[SOLVED] no sound with saa7134 tv card"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by ogcub on 2007-10-01
Hello, i have trouble getting sound from my tv card. It's Pixelview playtv mobile, PCMCIA, so sound need to be taken from pci bus.
lspci shows this
```
07:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
```

When card is initialized during boot up, dmesg shows usual no eeprom crap:
```
[   24.872000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   25.048000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[   25.048000] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   25.048000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 17, latency: 0, mmio: 0x34000000
[   25.048000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   25.048000] saa7134: <rant>
[   25.048000] saa7134:  Congratulations!  Your TV card vendor saved a few
[   25.048000] saa7134:  cents for a eeprom, thus your pci board has no
[   25.048000] saa7134:  subsystem ID and I can't identify it automatically
[   25.048000] saa7134: </rant>
[   25.048000] saa7134: I feel better now.  Ok, here are the good news:
[   25.048000] saa7134: You can use the card=<nr> insmod option to specify
[   25.048000] saa7134: which board do you have.  The list:
[   25.048000] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   25.048000] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   25.048000] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   25.048000] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   25.048000] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   25.048000] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   25.048000] saa7134:   card=6 -> Tevion MD 9717                          
[   25.048000] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   25.048000] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   25.048000] saa7134:   card=9 -> Medion 5044                             
[   25.048000] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   25.048000] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   25.048000] saa7134:   card=12 -> Medion 7134                              16be:0003
[   25.048000] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   25.048000] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   25.048000] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   25.048000] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   25.048000] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   25.048000] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   25.048000] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   25.048000] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   25.048000] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   25.048000] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   25.048000] saa7134:   card=23 -> BMK MPEX Tuner                          
[   25.048000] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   25.048000] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   25.048000] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   25.048000] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   25.048000] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[   25.048000] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   25.048000] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   25.048000] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   25.048000] saa7134:   card=32 -> AVACS SmartTV                           
[   25.048000] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   25.048000] saa7134:   card=34 -> Noval Prime TV 7133                     
[   25.048000] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   25.048000] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   25.048000] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   25.048000] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   25.048000] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   25.048000] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   25.048000] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   25.048000] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   25.048000] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   25.048000] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   25.048000] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   25.048000] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   25.048000] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   25.048000] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   25.048000] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   25.048000] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   25.048000] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   25.048000] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   25.048000] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   25.048000] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 1489:0214 5168:0304
[   25.048000] saa7134:   card=55 -> LifeView FlyDVB-T DUO                    5168:0306
[   25.048000] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   25.048000] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   25.048000] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   25.048000] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   25.048000] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   25.048000] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   25.048000] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   25.048000] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   25.048000] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   25.048000] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   25.048000] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   25.048000] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   25.048000] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   25.048000] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   25.048000] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   25.048000] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   25.048000] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   25.048000] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   25.048000] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   25.048000] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   25.048000] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   25.048000] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   25.048000] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4876
[   25.048000] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   25.048000] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   25.048000] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   25.048000] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   25.048000] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   25.048000] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   25.048000] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   25.048000] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   25.048000] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   25.048000] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   25.048000] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   25.048000] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[   25.048000] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   25.048000] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   25.048000] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   25.048000] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[   25.048000] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   25.048000] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   25.048000] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   25.048000] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   25.048000] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   25.048000] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   25.048000] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   25.048000] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   25.048000] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   25.048000] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   25.048000] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   25.048000] saa7134[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   25.048000] saa7134[0]: board init: gpio is e240c0
[   25.152000] saa7134[0]: Huh, no eeprom present (err=-5)?
[   25.152000] saa7134[0]: registered device video0 [v4l2]
[   25.152000] saa7134[0]: registered device vbi0
[   25.184000] saa7134 ALSA driver for DMA sound loaded
[   25.184000] saa7134[0]/alsa: saa7134[0] at 0x34000000 irq 17 registered as card -2

```

I know that my card should be identical to card 79 so i exec:
rmmod -f saa7134 saa7134-alsa

then i add saa again:
modprobe saa7134 card=79

after that dmesg shows some good stuff:
```
[ 3161.224000] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 3161.228000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 17, latency: 64, mmio: 0x34000000
[ 3161.228000] saa7134[0]: subsystem: 1131:0000, board: Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B) [card=79,insmod option]
[ 3161.228000] saa7134[0]: board init: gpio is 25d00
[ 3161.228000] input: saa7134 IR (Sedna/MuchTV PC TV  as /class/input/input8
[ 3161.420000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[ 3161.472000] tuner 0-004b: setting tuner address to 60
[ 3161.512000] tuner 0-004b: type set to tda8290+75a
[ 3161.624000] tuner 0-004b: setting tuner address to 60
[ 3161.664000] tuner 0-004b: type set to tda8290+75a
[ 3161.728000] saa7134[0]: Huh, no eeprom present (err=-5)?
[ 3164.160000] saa7134[0]: registered device video0 [v4l2]
[ 3164.160000] saa7134[0]: registered device vbi0
[ 3164.164000] saa7134[0]: registered device radio0
[ 3164.312000] saa7134 ALSA driver for DMA sound loaded
[ 3164.312000] saa7134[0]/alsa: saa7134[0] at 0x34000000 irq 17 registered as card -2

```

After this i can start tvtime, and scan channels. I get picture, but unfortunately no sound, not even noise. What i have done wrong? Please help

---

### Post by damir_1105 on 2007-10-05
i prepare litle how to. you can find it on [http://ubuntuforums.org/showthread.php?t=568528]("http://ubuntuforums.org/showthread.php?t=568528")

---

### Post by ogcub on 2007-10-08
thank you,
using tvtime and
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```
i get sound working, however after some time it goes way out of sync, and finally i get error in console: overrun!!! (at least XXXX ms long) . After that sound becomes choppy and crappy.  What do you suggest??

---

### Post by damir_1105 on 2007-10-08
i use combination of arecord and sox for best results. sync it's ok. try this.
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,1
```

---

### Post by ogcub on 2007-10-09
> **damir_1105 said:**
> i use combination of arecord and sox for best results. sync it's ok. try this.
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,1
```

Don;t work for me, i get
```

Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
sox: Failed writing hw:0,1: cannot open audio device

```

---

### Post by damir_1105 on 2007-10-09
first use:
```
aplay -l
```
to see list of  PCM playback devices.

if your primary card has index 0, that's mean hw:0,x
in the list locate second index, that will depend on number of inputs and outputs.
you can experiment with: hw:0,0 , hw:0,1 , hw:0,2 , hw:0,3, ...
index of your TV card is hw:1,0 and this is ok.
if you have second audio card index would be hw:2.0 and so on.

change only bold part in thist command:
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa **hw:0,1**
```

this should help.
sorry for bad english. :D

---

### Post by ogcub on 2007-10-10
> **damir_1105 said:**
> first use:
```
aplay -l
```
to see list of  PCM playback devices.

if your primary card has index 0, that's mean hw:0,x
in the list locate second index, that will depend on number of inputs and outputs.
you can experiment with: hw:0,0 , hw:0,1 , hw:0,2 , hw:0,3, ...
index of your TV card is hw:1,0 and this is ok.
if you have second audio card index would be hw:2.0 and so on.

change only bold part in thist command:
```
arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa **hw:0,1**
```

this should help.
sorry for bad english. :D

Thank you, hw:0,0 works for me. Now testing synchronization.

---

### Post by ogcub on 2007-10-10
Well kinda works ( although about 1s delay), but after some time I still get 
```
overrun!!! (at least 65.268 ms long)
``` and sound becomes choppy
Any suggestions?

---

### Post by ogcub on 2007-10-11
Partially solved using mplayer which can take alsa sound. However, no luck with arecord/aplay/sox

---

### Post by damir_1105 on 2007-10-11
maybe is problem with sound card driver, or something else, i have no idea. :D

I use pci tv card, and best result is direct connection to sound card input with 4 wire cable. (it comes with new CD ROM...) In this way you don't have to use DMA. if you have anything similar on your CardBus you can try.

---

### Post by gakna on 2008-02-06
Hi! (and sorry for my bad english:) i also cant get tvtime to play with sound (i have images though) when i tried the command line: arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0

it says: 

ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
arecord: main:545: audio open error: No such device
sox stio: Failed reading `-': WAVE: RIFF header not found

any ideas??

---


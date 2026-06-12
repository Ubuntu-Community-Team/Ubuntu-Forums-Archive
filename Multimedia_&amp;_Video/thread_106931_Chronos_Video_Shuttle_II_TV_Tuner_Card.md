---
title: "Chronos Video Shuttle II TV Tuner Card"
date: 2005-12-21
forum: Multimedia &amp; Video
---

### Post by carelburger on 2005-12-21
I've been struggeling around for about a day to try and get the card to work. It uses the very popular Philips Saa7130 Chipset which from what I know is supported under the SAA7134 driver for linux.

Ubuntu detects the card as follows :

[INDENT]Dec 21 23:12:14 localhost kernel: Linux video capture interface: v1.00
Dec 21 23:12:14 localhost kernel: saa7130/34: v4l2 driver version 0.2.12 loaded
Dec 21 23:12:14 localhost kernel: ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 22
Dec 21 23:12:14 localhost kernel: saa7130[0]: found at 0000:02:01.0, rev: 1, irq: 22, latency: 32, mmio: 0xfeaffc00
Dec 21 23:12:14 localhost kernel: saa7134: <rant>
Dec 21 23:12:14 localhost kernel: saa7134:  Congratulations!  Your TV card vendor saved a few
Dec 21 23:12:14 localhost kernel: saa7134:  cents for a eeprom, thus your pci board has no
Dec 21 23:12:14 localhost kernel: saa7134:  subsystem ID and I can't identify it automatically
Dec 21 23:12:14 localhost kernel: saa7134: </rant>
Dec 21 23:12:14 localhost kernel: saa7134: I feel better now.  Ok, here are the good news:
Dec 21 23:12:14 localhost kernel: saa7134: You can use the card=<nr> insmod option to specify
Dec 21 23:12:14 localhost kernel: saa7134: which board do you have.  The list:
Dec 21 23:12:14 localhost kernel: saa7134:   card=0 -> UNKNOWN/GENERIC                         
Dec 21 23:12:14 localhost kernel: saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
Dec 21 23:12:14 localhost kernel: saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
Dec 21 23:12:14 localhost kernel: saa7134:   card=3 -> LifeView FlyVIDEO2000                    5168:0138
Dec 21 23:12:14 localhost kernel: saa7134:   card=4 -> EMPRESS                                  1131:6752
Dec 21 23:12:14 localhost kernel: saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
Dec 21 23:12:14 localhost kernel: saa7134:   card=6 -> Tevion MD 9717                          
Dec 21 23:12:14 localhost kernel: saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
Dec 21 23:12:14 localhost kernel: saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
Dec 21 23:12:14 localhost kernel: saa7134:   card=9 -> Medion 5044                             
Dec 21 23:12:14 localhost kernel: saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
Dec 21 23:12:14 localhost kernel: saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
Dec 21 23:12:14 localhost kernel: saa7134:   card=12 -> Medion 7134                              16be:0003
Dec 21 23:12:14 localhost kernel: saa7134:   card=13 -> Typhoon TV+Radio 90031                  
Dec 21 23:12:14 localhost kernel: saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
Dec 21 23:12:14 localhost kernel: saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226b
Dec 21 23:12:14 localhost kernel: saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
Dec 21 23:12:14 localhost kernel: saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
Dec 21 23:12:14 localhost kernel: saa7134:   card=18 -> BMK MPEX No Tuner                       
Dec 21 23:12:14 localhost kernel: saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
Dec 21 23:12:14 localhost kernel: saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
Dec 21 23:12:14 localhost kernel: saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
Dec 21 23:12:14 localhost kernel: saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
Dec 21 23:12:14 localhost kernel: saa7134:   card=23 -> BMK MPEX Tuner                          
Dec 21 23:12:14 localhost kernel: saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
Dec 21 23:12:14 localhost kernel: saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
Dec 21 23:12:14 localhost kernel: saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b 11bd:002d
Dec 21 23:12:14 localhost kernel: saa7134:   card=27 -> Manli MuchTV M-TV002                    
Dec 21 23:12:14 localhost kernel: saa7134:   card=28 -> Manli MuchTV M-TV001                    
Dec 21 23:12:14 localhost kernel: saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
Dec 21 23:12:14 localhost kernel: saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
Dec 21 23:12:14 localhost kernel: saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
Dec 21 23:12:14 localhost kernel: saa7134:   card=32 -> AVACS SmartTV                           
Dec 21 23:12:14 localhost kernel: saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
Dec 21 23:12:14 localhost kernel: saa7134:   card=34 -> Noval Prime TV 7133                     
Dec 21 23:12:14 localhost kernel: saa7134:   card=35 -> AverMedia 305                            1461:2115
Dec 21 23:12:14 localhost kernel: saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
Dec 21 23:12:14 localhost kernel: saa7134:   card=37 -> Items MuchTV Plus / IT-005              
Dec 21 23:12:14 localhost kernel: saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
Dec 21 23:12:14 localhost kernel: saa7134:   card=39 -> LifeView FlyTV Platinum                  5168:0212
Dec 21 23:12:14 localhost kernel: saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
Dec 21 23:12:14 localhost kernel: saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
Dec 21 23:12:14 localhost kernel: saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
Dec 21 23:12:14 localhost kernel: saa7134:   card=43 -> :Zolid Xpert TV7134                     
Dec 21 23:12:14 localhost kernel: saa7134:   card=44 -> Empire PCI TV-Radio LE                  
Dec 21 23:12:14 localhost kernel: saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
Dec 21 23:12:14 localhost kernel: saa7134:   card=46 -> AVerMedia Cardbus TV/Radio               1461:d6ee
Dec 21 23:12:14 localhost kernel: saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
Dec 21 23:12:14 localhost kernel: saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
Dec 21 23:12:14 localhost kernel: saa7130[0]: board init: gpio is c0c000
Dec 21 23:12:14 localhost kernel: saa7130[0]: Huh, no eeprom present (err=-5)?
Dec 21 23:12:14 localhost kernel: saa7130[0]: registered device video0 [v4l2]
Dec 21 23:12:14 localhost kernel: saa7130[0]: registered device vbi0[/INDENT]

From what I learned when I googled for solutions I followed the following commands to try and get the card to work since it does not know what version of the card I've put in the computer. Since I've got card number 35 I used the following commands

[INDENT]sudo rmmod bttv[INDENT]To unload bttv[/INDENT]
sudo modprobe bttv card=35
[/INDENT]

After all of this I still get the same output. What I noticed is that it is supposed to detect a tuner, since it is a tv tuner card. It does not detect it. I tried my luck with *sudo modprobe tuner* but with no luck!

How would I know if the driver actually works? I am using *tvtime* to try and watch tv. It just keeps giving me the default input mode.

Any suggestions?

---

### Post by hellfire_bg on 2006-01-21
You shouldn`t modprobe bttv. Instead you should modprobe saa7134. To get it working i did this:
1st instal tvtime (this is my favourite tv program)
2nd modprobe saa7134 card=3 (if you`re using the variant with radio the card number may be different)
3rd tvtime-scanner (to scan for channels)
4th (if the above didn`t work) rmmod saa7134 and then modprobe saa7134 card =3 again. I don`t know why but it has effect.

---

### Post by rbarryza on 2007-09-02
Did anyone get this card working?  I have the Chronos Video Shuttle II with FM radio (PAL/SECAM) .  It has the Philips 7134 chipset.  I can't get it to work 100%, and it's bugging the hell out of me!  I've tried many different combinations of card= and tuner= when installing the module with modprobe.  It looks like it should work with card=2, but I have no idea what tuner to use.  When I do:
modprobe saa7134 card=2 tuner=38
I get pictures on Composite 2 (using waxtv or tvtime), Television gives a blue screen with "No Signal".   Using xawtv, I can tune to most channels, but the sound is only noise.  When I fine tune the channel, I get perfect sound, but only after the picture disappears.  I'm guessing I'm using the wrong tuner, which causes the tuner to extract the sound from the wrong freq band.  

Some more info on the specific card:
Chip on the front of the card : SAA7135HL/203

Printed on the back:
IT023 Rev:4E
P/N: 123-00004
S/N: 070129002-0245

PC TV PCI/7135
PAL SECAM TV FM
<Barcode>
0232007021211

I've taken pictures of the front and back, they can be seen here:
Front: [http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0317.jpg](http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0317.jpg)
Back: [http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0318.jpg](http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0318.jpg)

Has anyone else gotten this card to work?  I'm desperate!

---

### Post by rbarryza on 2007-09-02
modprobe 7134 card=2 tuner=38
dmesg

gives:

[  611.491918] saa7130/34: v4l2 driver version 0.2.14 loaded
[  611.493732] saa7133[0]: found at 0000:00:0a.0, rev: 209, irq: 17, latency: 32, mmio: 0xe1105000
[  611.493744] saa7133[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[  611.493856] saa7133[0]: board init: gpio is 608000
[  611.493859] saa7133[0]: there are different flyvideo cards with different tuners
[  611.493861] saa7133[0]: out there, you might have to use the tuner=<nr> insmod
[  611.493863] saa7133[0]: option to override the default value.
[  611.495726] input: saa7134 IR (LifeView FlyVIDEO30 as /class/input/input9
[  611.623592] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  611.623601] tuner 0-0060: chip found @ 0xc0 (saa7133[0])
[  611.625398] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[  611.625407] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[  611.628041] saa7133[0]: Huh, no eeprom present (err=-5)?
[  611.658136] saa7133[0]: registered device video0 [v4l2]
[  611.660503] saa7133[0]: registered device vbi0
[  611.662414] saa7133[0]: registered device radio0
[  611.675703] saa7134 ALSA driver for DMA sound loaded
[  611.675755] saa7133[0]/alsa: saa7133[0] at 0xe1105000 irq 17 registered as card -2

---

### Post by the_mouse on 2007-09-20
I'm having the same problem - It seems that we are not using the right combination of card and tuner options, I'll keep looking for it and will post here if I succeed ;)

---

### Post by aPello on 2007-10-14
[http://www.amazon.com/Philips-SAA7130-Tuner-Radio-Capture/dp/B000I6C3XI](http://www.amazon.com/Philips-SAA7130-Tuner-Radio-Capture/dp/B000I6C3XI)
I have that version of the same card, and am having the same problem.

---

### Post by laigor on 2008-05-17
> **rbarryza said:**
> Did anyone get this card working?  I have the Chronos Video Shuttle II with FM radio (PAL/SECAM) .  It has the Philips 7134 chipset.  I can't get it to work 100%, and it's bugging the hell out of me!  I've tried many different combinations of card= and tuner= when installing the module with modprobe.  It looks like it should work with card=2, but I have no idea what tuner to use.  When I do:
modprobe saa7134 card=2 tuner=38
I get pictures on Composite 2 (using waxtv or tvtime), Television gives a blue screen with "No Signal".   Using xawtv, I can tune to most channels, but the sound is only noise.  When I fine tune the channel, I get perfect sound, but only after the picture disappears.  I'm guessing I'm using the wrong tuner, which causes the tuner to extract the sound from the wrong freq band.  

Some more info on the specific card:
Chip on the front of the card : SAA7135HL/203

Printed on the back:
IT023 Rev:4E
P/N: 123-00004
S/N: 070129002-0245

PC TV PCI/7135
PAL SECAM TV FM
<Barcode>
0232007021211

I've taken pictures of the front and back, they can be seen here:
Front: [http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0317.jpg](http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0317.jpg)
Back: [http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0318.jpg](http://i84.photobucket.com/albums/k18/pienkzuit/IMG_0318.jpg)

Has anyone else gotten this card to work?  I'm desperate!

I have the same card.
It began to work with card=42 and tuner=38. Also it work with card=67 and card=100. Also tuner may be set to 63.

---

### Post by Nsangu on 2008-06-13
Please How can the drivers for a tv card saa7135 chronous

---

### Post by Nsangu on 2008-06-14
> **Nsangu said:**
> Please How can the drivers for a tv card saa7135 chronous

Pls I need a driver for SAA 7135 Tv Card

---

### Post by Nsangu on 2008-06-14
> **Nsangu said:**
> Please How can the drivers for a tv card saa7135 chronous

Pls I need a driver for SAA 7135 Tv Card
Thanks you
Rigobert Nsangu

---


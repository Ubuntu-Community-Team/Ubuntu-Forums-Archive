---
title: "How to get tv time to see my card"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by ShirishAg75 on 2006-07-26
Hi all,
       I want to see TV on my comp. Due to suggestions I've installed tv timer to see it but nothing seems to be happening. The card has been recognised as can be seen from lspci which was posted here . Furthermore, I've got the following from looking at the /var/log/syslog details:-

> Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134: <rant>
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:  Congratulations!  Your TV card vendor saved a few
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:  cents for a eeprom, thus your pci board has no
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:  subsystem ID and I can't identify it automatically
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134: </rant>
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134: I feel better now.  Ok, here are the good news:
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134: You can use the card=<nr> insmod option to specify
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134: which board do you have.  The list:
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=0 -> UNKNOWN/GENERIC
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1$Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4$Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=3 -> LifeView FlyVIDEO2000                    5168:0138
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=4 -> EMPRESS                                  1131:6752
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=6 -> Tevion MD 9717
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1$Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=9 -> Medion 5044
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=12 -> Medion 7134                              16be:0003
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=13 -> Typhoon TV+Radio 90031
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226b
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 $Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=18 -> BMK MPEX No Tuner
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=23 -> BMK MPEX Tuner
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=32 -> AVACS SmartTV
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134:   card=34 -> Noval Prime TV 7133 
 It goes to show around 70 odd cards which share the same chipset. After that I get this :-

> 
Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodete$Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7130[0]: board init: gpio is 38500
Jul 26 11:54:55 localhost kernel: [17179594.976000] eth0: link down
Jul 26 11:54:55 localhost kernel: [17179595.028000] saa7130[0]: Huh, no eeprom present (err=-5)?
Jul 26 11:54:55 localhost kernel: [17179595.028000] saa7130[0]: registered device video0 [v4l2]
Jul 26 11:54:55 localhost kernel: [17179595.028000] saa7130[0]: registered device vbi0
Jul 26 11:54:55 localhost kernel: [17179595.056000] saa7134 ALSA driver for DMA sound loaded
Jul 26 11:54:55 localhost kernel: [17179595.056000] saa7130[0]/alsa: saa7130[0] at 0xdfdffc00 irq 217 registered as card -1 
    Now in windows, I've been able to work with it successfully with using the Lifevideo Prime 30 card driver which seems to be driver 2 . Don't know about driver 1. So what should I do or how should I go about it?

    Another thing I live in India so need to make it PAL-B which is the standard for television broadcast here. All help & guidance appreciated. 
            Thnx in advance.

---

### Post by ShirishAg75 on 2006-07-26
Got the following at tvtime's [site]("http://tvtime.sourceforge.net/problems.html#undetected") :-


> **6. Unable to tune to channels using the             bttv, saa7134 or cx88 drivers**

          The bttv, saa7134, and cx88 drivers each support a wide variety         of cards which all use the same chip.  In particular, these cards         differ in what tuner they use, how many inputs they have, and how         it is configured.
          Often, these drivers cannot autodetect the card type, or detect         the incorrect card.  To debug this, you must watch your kernels logs         by running the "dmesg" command, potentially loading and         unloading the driver with different options until the driver is         successfully loaded.
          Some hints:
         [LIST=1]
[*]If your card appears as UNKNOWN/GENERIC, then the             tuner driver will not be loaded and the card will likely not             work.  You will need to load the driver with the correct card             number.
[*]If your tuner reports that it is using type -1, it is not loaded             and you will not be able to tune any stations.
[*]If you are an NTSC user, make sure the tuner you are using announces             itself as an NTSC tuner.[/LIST]


   Now I know some more things , I'm in India which has PAL-B India=91 

   Just looking for tips & things to take care of while doing this things.

---

### Post by ShirishAg75 on 2006-07-27
Come on guys, somebody please tell me something.

---

### Post by cblanquer on 2006-07-27
Hi,

I also had trouble for my card, finally got it working - beware sound trouble, this is the worst.

Follow the instructions you got:
> Jul 26 11:54:55 localhost kernel: [17179594.924000] saa7134: You can use the card=<nr> insmod option to specify

Or rather use "modprobe".

You shoud identify wich is the driver for your card. 
Open a terminal and try > modprobe <card driver> card=<n> 
For instance > modprobe saa7134 card=2 There is a parameter for the tuner you probably will have to set as well:
> modprobe <card driver> card=<n> tuner=<m>
If it does not work try other that can be likely to work. Search you card's manufaturer site or googelize it to discover them.

When you get it working then you have to ensure to load the proper module at start up, I guess it is including the same command in /etc/modules (no time to check right now but it is something easy to do).

Search more tvtime website and remember to take some notes to know the steps done before.
I hope this helps.

---

### Post by ShirishAg75 on 2006-08-03
>  			 				modprobe <card driver> card=<n> tuner=<m>

what is the tuner option for & what should I enter there?

---

### Post by cblanquer on 2006-08-04
Definitely take some time to read [http://www.linuxtv.org/](http://www.linuxtv.org/) : it is the only way to understand how it works and get to find specific solutions.
For instance have a look to [http://www.linuxtv.org/v4lwiki/index.php/Tuners](http://www.linuxtv.org/v4lwiki/index.php/Tuners).

Good luck.8)

---


---
title: "TV Tunner"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by Dan-Paul-C on 2008-03-30
Hi all. I can't install my TV Tunner. I search a lot and I don't find the solution. I also ask to [www.ubuntu-fr.org](www.ubuntu-fr.org) and [www.linuxpourlesnuls.org](www.linuxpourlesnuls.org), but they don't know how to help me. 

So, my TV Tunner is a Super Digital Video (Glaring Series) and I'm running Ubuntu Gutsy.

lspci:
[html].....
04:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)[/html]

dmesg:
[html].....
[   35.103290] input: PC Speaker as /class/input/input3
[   35.200018] parport_pc 00:06: reported by Plug and Play ACPI
[   35.200114] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   35.287664] Linux video capture interface: v2.00
[   35.328685] nvidia: module license 'NVIDIA' taints kernel.
[   35.586530] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.586538] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   35.586604] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   35.611851] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.611860] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   35.611867] atl1 0000:02:00.0: version 2.0.7
[   35.621883] iTCO_vendor_support: vendor-support=0
[   35.635247] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   35.649737] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX)
[   35.669308] saa7130/34: v4l2 driver version 0.2.14 loaded
[   35.706369] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.706376] saa7130[0]: found at 0000:04:01.0, rev: 1, irq: 16, latency: 64, mmio: 0xfebff800
[   35.706382] saa7134:
[   35.706382] saa7134:  Congratulations!  Your TV card vendor saved a few
[   35.706383] saa7134:  cents for a eeprom, thus your pci board has no
[   35.706384] saa7134:  subsystem ID and I can't identify it automatically
[   35.706385] saa7134:
[   35.706386] saa7134: I feel better now.  Ok, here are the good news:
[   35.706387] saa7134: You can use the card= insmod option to specify
[   35.706387] saa7134: which board do you have.  The list:
[   35.706390] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   35.706392] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   35.706395] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   35.706398] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   35.706401] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   35.706403] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   35.706406] saa7134:   card=6 -> Tevion MD 9717                         
[   35.706408] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   35.706411] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   35.706413] saa7134:   card=9 -> Medion 5044                             
[   35.706415] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI     
[   35.706417] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   35.706419] saa7134:   card=12 -> Medion 7134                              16be:0003
[   35.706422] saa7134:   card=13 -> Typhoon TV+Radio 90031                 
[   35.706424] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   35.706426] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   35.706428] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   35.706432] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   35.706434] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   35.706436] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   35.706438] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   35.706441] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   35.706443] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   35.706445] saa7134:   card=23 -> BMK MPEX Tuner                         
[   35.706447] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   35.706450] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   35.706452] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   35.706454] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   35.706456] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401     
[   35.706458] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   35.706461] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   35.706463] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   35.706465] saa7134:   card=32 -> AVACS SmartTV                           
[   35.706467] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   35.706470] saa7134:   card=34 -> Noval Prime TV 7133                     
[   35.706472] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   35.706474] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   35.706476] saa7134:   card=37 -> Items MuchTV Plus / IT-005             
[   35.706478] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   35.706481] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   35.706484] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   35.706486] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   35.706488] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)             
[   35.706490] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   35.706492] saa7134:   card=44 -> Empire PCI TV-Radio LE                 
[   35.706494] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   35.706496] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   35.706499] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   35.706501] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   35.706503] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   35.706506] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   35.706508] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   35.706511] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   35.706513] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   35.706515] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   35.706519] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   35.706522] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   35.706524] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   35.706527] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   35.706530] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
[   35.706532] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   35.706536] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   35.706538] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   35.706540] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   35.706542] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   35.706544] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   35.706546] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                 
[   35.706548] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   35.706550] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   35.706553] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   35.706555] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   35.706558] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   35.706560] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   35.706562] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   35.706565] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   35.706567] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   35.706569] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   35.706572] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   35.706574] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   35.706577] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   35.706579] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   35.706582] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   35.706584] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   35.706587] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   35.706589] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   35.706591] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   35.706594] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   35.706597] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   35.706600] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   35.706602] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   35.706604] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[   35.706607] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   35.706609] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   35.706612] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   35.706614] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[   35.706617] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   35.706619] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   35.706622] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   35.706625] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   35.706627] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   35.706630] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   35.706632] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   35.706635] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   35.706637] saa7134:   card=103 -> Compro Videomate DVB-T200A             
[   35.706639] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   35.706641] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   35.706644] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   35.706647] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   35.706650] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   35.706652] saa7134:   card=109 -> Philips Tiger - S Reference design     
[   35.706654] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   35.706656] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   35.706659] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   35.706661] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   35.706664] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   35.706666] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   35.706669] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   35.706675] saa7130[0]: board init: gpio is 804000
[   35.721977] atl1 0000:02:00.0: Unable to enable MSI: -22
[   35.822702] saa7130[0]: Huh, no eeprom present (err=-5)?
[   35.822833] saa7130[0]: registered device video0 [v4l2]
[   35.822930] saa7130[0]: registered device vbi0
[   35.903387] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   35.903399] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   35.946570] saa7134 ALSA driver for DMA sound loaded
[   35.946588] saa7130[0]/alsa: saa7130[0] at 0xfebff800 irq 16 registered as card -2
.....[/html]

lspci -s 04:01.0 -n:
[HTML]04:01.0 0480: 1131:7130 (rev 01)[/HTML]

lspci -s 04:01.0 -v:
[HTML]04:01.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors Unknown device 0000
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at febff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1[/HTML]

dmesg | tail -n 20:
[HTML][ 1224.614803] saa7134 ALSA driver for DMA sound loaded
[ 1224.614972] saa7130[0]/alsa: saa7130[0] at 0xfebff800 irq 16 registered as card -2
[ 1582.006759] saa7134 ALSA driver for DMA sound unloaded
[ 1706.681031] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 1706.681484] saa7130[0]: found at 0000:04:01.0, rev: 1, irq: 16, latency: 64, mmio: 0xfebff800
[ 1706.681490] saa7130[0]: subsystem: 1131:0000, board: Compro VideoMate TV PVR/FM [card=40,insmod option]
[ 1706.681497] saa7130[0]: board init: gpio is 44000
[ 1706.682275] input: saa7134 IR (Compro VideoMate TV as /class/input/input8
[ 1706.799484] tuner 0-0060: All bytes are equal. It is not a TEA5767
[ 1706.799488] tuner 0-0060: chip found @ 0xc0 (saa7130[0])
[ 1706.799788] tuner 0-0060: type set to 17 (Philips NTSC_M (MK2))
[ 1706.799790] tuner 0-0060: type set to 17 (Philips NTSC_M (MK2))
[ 1706.807491] tuner 0-0061: chip found @ 0xc2 (saa7130[0])
[ 1706.810670] saa7130[0]: Huh, no eeprom present (err=-5)?
[ 1706.814240] saa7130[0]: registered device video0 [v4l2]
[ 1706.814382] saa7130[0]: registered device vbi0
[ 1706.814495] saa7130[0]: registered device radio0
[ 1706.832024] saa7134 ALSA driver for DMA sound loaded
[ 1706.832044] saa7130[0]/alsa: saa7130[0] at 0xfebff800 irq 16 registered as card -2
[ 2389.543277] saa7134 ALSA driver for DMA sound unloaded [/HTML]

ls -lR /dev/dvb/:
[HTML]ls: /dev/dvb/: Aucun fichier ou répertoire de ce type[/HTML]

Please help me to find my driver. Have all a nice day!

---

### Post by mrpixels0 on 2008-03-30
Hi there Dan-Paul-C

your card is very close to mine try this:

[http://ubuntuforums.org/showthread.php?p=4506840#post4506840](http://ubuntuforums.org/showthread.php?p=4506840#post4506840)

follow these instructions and see if it fixes it, if not post back and i will try to help you more.

MP0

---

### Post by Dan-Paul-C on 2008-03-31
Thank you for your answer, but the steep 3 doesn't work:
[HTML]danpaulc@danpaulc-desktop:~$ sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa1734
FATAL: Module saa1734 not found.[/HTML]
Please help me. Have a nice day!

---

### Post by mrpixels0 on 2008-04-01
Hey there Dan-Paul-C,

It is built in to the Kernel so that step should not be needed ;).

is your TV/FM card Digital or Analog ?.

if it is Digital the your saa1734 file in the /etc/modprobe.d directory should look like this:

alias chr-major-81 videodev
alias chr-major-81-0 saa7134-dvb
options saa7134 card=42 tuner=43 

now if you want you can build a new saa1734.ko module by following these instructions below:

go here : [HTTp://linuxtv.org/hg/v4l-dvb](HTTp://linuxtv.org/hg/v4l-dvb)

and get a file named : v4l-dvb-8dd55a231e6a.tar.gz

(on the page you will see orange writting, look to the far right and you will see gz written in orange get that file)

open a terminal and type : sudo apt-get install mercurial linux-headers-$(uname -r)build-essential and press enter.

then extract the file you just downloaded and cd in to the directory it created when it extracted and from a terminal type : sudo make (wait for it to finish) and then type sudo make install.

then issue the following commandfrom a terminal: 
sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa1734 

and that should put it right and working good, use tvtime as your viewer it works well and is easy to configure. and I Like Gnome radio as my radio tuner program also easy to configure.

Try that and see if it works for you it did for me.

Note: somtimes a reboot is needed for this to work, should not be needed but sometimes it can help.

MP0

---

### Post by Dan-Paul-C on 2008-04-01
Hi! I have downloaded this file: "v4l-dvb-0776e4801991", not "v4l-dvb-8dd55a231e6a" because I can't see it. I have install it, but when I type "sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa1734 " it says: "ERROR: Module saa7134_alsa does not exist in /proc/modules"; And I don't have the radio on my card, only the TV. Are you sure that our cards are close? Thank you for helping me!

---

### Post by prshah on 2008-04-01
> **Dan-Paul-C said:**
> Thank you for your answer, but the [color=red]steep[/color] 3 doesn't work:
danpaulc@danpaulc-desktop:~$ sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe **[color=red]saa1734[/color]**
FATAL: Module **[color=red]saa1734[/color]** not found.
Please help me. Have a nice day!

Typo. Please correct spelling to saa[color=blue]7134[/color]

---

### Post by Dan-Paul-C on 2008-04-01
Hi! Ok, now I have this error:
[HTML]danpaulc@danpaulc-desktop:~$ sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa7134
ERROR: Module saa7134_alsa does not exist in /proc/modules[/HTML]
Please help me. Have a nice day!

---

### Post by Dan-Paul-C on 2008-04-03
up

---

### Post by fernando on 2008-04-04
> **Dan-Paul-C said:**
> Hi! Ok, now I have this error:
[HTML]danpaulc@danpaulc-desktop:~$ sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa7134
ERROR: Module saa7134_alsa does not exist in /proc/modules[/HTML]
Please help me. Have a nice day!

What's your Ubuntu Version? if you're on 8.04 beta, notice that the saa7134_alsa has not been compiled as a module for the stock generic kernel. you'll probably have to wait for another release or compile a kernel on your own.

Regards,

Fernando

---

### Post by prshah on 2008-04-06
> **Dan-Paul-C said:**
> Hi! Ok, now I have this error:
[HTML]danpaulc@danpaulc-desktop:~$ sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa7134
ERROR: Module saa7134_alsa does not exist in /proc/modules[/HTML]
Please help me. Have a nice day!

Hey this error is normal, it's coming because you tried to rmmod a module that is not actually loaded. It have nothing to do with your problem.

---

### Post by MerrickB on 2008-05-18
> **Dan-Paul-C said:**
> Thank you for your answer, but the steep 3 doesn't work:
[HTML]danpaulc@danpaulc-desktop:~$ sudo rmmod saa7134_alsa && sudo rmmod saa7134 && modprobe saa1734
FATAL: Module saa1734 not found.[/HTML]
Please help me. Have a nice day!

I'm having a similar problem here.  While I followed the instruction on creating the saa7134.save file I get a picture but no sound.  Checked the dmesg information and came across this:

[   34.197919] saa7134 ALSA: can't load, DMA sound handler already assigned (probably to OSS)

Which leads me to suspect that it might have something to do with the sound not coming through. Am I on the right track?  And more importantly how do I fix this?  

Currently running Hardy distro, with a SoundBlaster Audigy LS PCI sound card.

---


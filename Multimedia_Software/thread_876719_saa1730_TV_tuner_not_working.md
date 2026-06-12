---
title: "saa1730 TV tuner not working"
date: 2008-08-01
forum: Multimedia Software
---

### Post by zfreak7c5 on 2008-08-01
I didn't search to well [http://ubuntuforums.org/showthread.php?t=723111&highlight=saa1734]("http://ubuntuforums.org/showthread.php?t=723111&highlight=saa1734")

Hello, I have TV tuner card that when I use the command lspci is recognized as Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01).  I have been trying to get it set up in MythTv and TVtime without success.  One thing I have noticed is that MythTv recognizes it as using the saa1734 driver so I blacklisted that and then the card was not recognized at all by MythTV.  Does anyone know how to get it to work.  Some of the reviews at [newegg ]("http://www.newegg.com/Product/ProductReview.aspx?Item=15-276-002&SortField=0&SummaryType=0&Pagesize=100&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&Keywords=&Page=") said it worked in Linux, but I have not gotten it to. 


        Thanks,

---

### Post by occupaja1 on 2009-07-11
hi am a beginner in ubuntu. i have connected my philips saa 1734 tv card to my acer laptop and i dont know what to do to make it work after using both xawtv and tvtime. am from ghana. please help me and my email address is [email]occupaja1@yahoo.com[/email]

---

### Post by HappyFeet on 2009-07-11
[This]("http://www.linuxtv.org/wiki/index.php/Saa713x_devices") may help.

---

### Post by zfreak7c5 on 2009-07-11
This is what worked for my card that uses the same driver.
open a terminal and run the following commands in order.  The numbers listed don't match my card either, but they still worked.

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe saa7134 card=42 tuner=43

test tvtime, you will need to change the input device in the menu

if it works, to make it stay on boot do the following

sudo gedit /etc/modprobe.d/blacklist.conf

add the following line to the bottom of the file and save, should work after reboots now

blacklist saa7134


I hope this helps,


Zach

---

### Post by xVehemencityx on 2010-04-24
Hi.  I hate bringing up a really old post, but it seems like this would be the best place to post it.  When I type sudo modprobe saa1734, I get this error.

> WARNING: All config files need .conf: /etc/modprobe.d/saa1734, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/saa1734, it will be ignored in a future release.
FATAL: Error inserting saa7134 (/lib/modules/2.6.32-21-generic/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134


---

### Post by alaukikyo on 2010-09-04
> **xVehemencityx said:**
> Hi.  I hate bringing up a really old post, but it seems like this would be the best place to post it.  When I type sudo modprobe saa1734, I get this error.
i have the same issue i started a new thread see [here]("http://ubuntuforums.org/showthread.php?t=1567212")

---

### Post by Peter J Schoen on 2011-04-26
I have a Compro VideoMate T100 sets up on all Windows without prob's to receive Australian Pal signals, but via Ubuntu it gets detected as a Compro T200 as per the below details, but it doesn't work..
the card is based on the Philips saa7130 chip, and over what seems weeks I think I have exhausted all avenues into getting this card going.. :(

I am running the latest Ubuntu 10:10 and as far as I am aware everything is the latest versions..

Mind you I am a Noob! so maybe I have missed something?:)   

Details of what Ubuntu detects the Compro T100 as 
--------------------------------------------------------------------------------------------------------------------------------

00:0b.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
    Subsystem: Compro Technology, Inc. Videomate DVB-T200 [185b:c901]
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at ee000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

--------------------------------------------------------------------------------------------------------------------------------
So what is everone doing to get their Compro T100 to go?

Thanks in advance..

---

### Post by crazups on 2011-04-27
> **Peter J Schoen said:**
> I have a Compro VideoMate T100 sets up on all Windows without prob's to receive Australian Pal signals, but via Ubuntu it gets detected as a Compro T200 as per the below details, but it doesn't work..
the card is based on the Philips saa7130 chip, and over what seems weeks I think I have exhausted all avenues into getting this card going.. :(

I am running the latest Ubuntu 10:10 and as far as I am aware everything is the latest versions..

Mind you I am a Noob! so maybe I have missed something?:)   

Details of what Ubuntu detects the Compro T100 as 
--------------------------------------------------------------------------------------------------------------------------------

00:0b.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
    Subsystem: Compro Technology, Inc. Videomate DVB-T200 [185b:c901]
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at ee000000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

--------------------------------------------------------------------------------------------------------------------------------
So what is everone doing to get their Compro T100 to go?

Thanks in advance..
Peter,

Have you tried sudo modprobe saa7134 card=71 tuner=41

Here is a list of card and tuner number that might help if you haven't seen this list already:

Card:

0 -> UNKNOWN/GENERIC
1 -> Proteus Pro [philips reference design] [1131:2001,1131:2001]
2 -> LifeView FlyVIDEO3000 [5168:0138,4e42:0138]
3 -> LifeView/Typhoon FlyVIDEO2000 [5168:0138,4e42:0138]
4 -> EMPRESS [1131:6752]
5 -> SKNet Monster TV [1131:4e85]
6 -> Tevion MD 9717
7 -> KNC One TV-Station RDS / Typhoon TV Tuner RDS [1131:fe01,1894:fe01]
8 -> Terratec Cinergy 400 TV [153b:1142]
9 -> Medion 5044
10 -> Kworld/KuroutoShikou SAA7130-TVPCI
11 -> Terratec Cinergy 600 TV [153b:1143]
12 -> Medion 7134 [16be:0003]
13 -> Typhoon TV+Radio 90031
14 -> ELSA EX-VISION 300TV [1048:226b]
15 -> ELSA EX-VISION 500TV [1048:226a]
16 -> ASUS TV-FM 7134 [1043:4842,1043:4830,1043:4840]
17 -> AOPEN VA1000 POWER [1131:7133]
18 -> BMK MPEX No Tuner
19 -> Compro VideoMate TV [185b:c100]
20 -> Matrox CronosPlus [102B:48d0]
21 -> 10MOONS PCI TV CAPTURE CARD [1131:2001]
22 -> AverMedia M156 / Medion 2819 [1461:a70b]
23 -> BMK MPEX Tuner
24 -> KNC One TV-Station DVR [1894:a006]
25 -> ASUS TV-FM 7133 [1043:4843]
26 -> Pinnacle PCTV Stereo (saa7134) [11bd:002b]
27 -> Manli MuchTV M-TV002/Behold TV 403 FM
28 -> Manli MuchTV M-TV001/Behold TV 401
29 -> Nagase Sangyo TransGear 3000TV [1461:050c]
30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card(PAL-BG,FM) [1019:4cb4]
31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card (NTSC,FM) [1019:4cb5]
32 -> AVACS SmartTV
33 -> AVerMedia DVD EZMaker [1461:10ff]
34 -> Noval Prime TV 7133
35 -> AverMedia AverTV Studio 305 [1461:2115]
36 -> UPMOST PURPLE TV [12ab:0800]
37 -> Items MuchTV Plus / IT-005
38 -> Terratec Cinergy 200 TV [153b:1152]
39 -> LifeView FlyTV Platinum Mini [5168:0212,4e42:0212]
40 -> Compro VideoMate TV PVR/FM [185b:c100]
41 -> Compro VideoMate TV Gold+ [185b:c100]
42 -> Sabrent SBT-TVFM (saa7130)
43 -> :Zolid Xpert TV7134
44 -> Empire PCI TV-Radio LE
45 -> Avermedia AVerTV Studio 307 [1461:9715]
46 -> AVerMedia Cardbus TV/Radio (E500) [1461:d6ee]
47 -> Terratec Cinergy 400 mobile [153b:1162]
48 -> Terratec Cinergy 600 TV MK3 [153b:1158]
49 -> Compro VideoMate Gold+ Pal [185b:c200]
50 -> Pinnacle PCTV 300i DVB-T + PAL [11bd:002d]
51 -> ProVideo PV952 [1540:9524]
52 -> AverMedia AverTV/305 [1461:2108]
53 -> ASUS TV-FM 7135 [1043:4845]
54 -> LifeView FlyTV Platinum FM / Gold [5168:0214,1489:0214,5168:0304]
55 -> LifeView FlyDVB-T DUO [5168:0306]
56 -> Avermedia AVerTV 307 [1461:a70a]
57 -> Avermedia AVerTV GO 007 FM [1461:f31f]
58 -> ADS Tech Instant TV (saa7135) [1421:0350,1421:0351,1421:0370,1421:1370]
59 -> Kworld/Tevion V-Stream Xpert TV PVR7134
60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Cardbus [5168:0502,4e42:0502,1489:0502]
61 -> Philips TOUGH DVB-T reference design [1131:2004]
62 -> Compro VideoMate TV Gold+II
63 -> Kworld Xpert TV PVR7134
64 -> FlyTV mini Asus Digimatrix [1043:0210]
65 -> V-Stream Studio TV Terminator
66 -> Yuan TUN-900 (saa7135)
67 -> Beholder BeholdTV 409 FM [0000:4091]
68 -> GoTView 7135 PCI [5456:7135]
69 -> Philips EUROPA V3 reference design [1131:2004]
70 -> Compro Videomate DVB-T300 [185b:c900]
71 -> Compro Videomate DVB-T200 [185b:c901]
72 -> RTD Embedded Technologies VFG7350 [1435:7350]
73 -> RTD Embedded Technologies VFG7330 [1435:7330]
74 -> LifeView FlyTV Platinum Mini2 [14c0:1212]
75 -> AVerMedia AVerTVHD MCE A180 [1461:1044]
76 -> SKNet MonsterTV Mobile [1131:4ee9]
77 -> Pinnacle PCTV 40i/50i/110i (saa7133) [11bd:002e]
78 -> ASUSTeK P7131 Dual [1043:4862,1043:4876]
79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B)
80 -> ASUS Digimatrix TV [1043:0210]
81 -> Philips Tiger reference design [1131:2018]
82 -> MSI TV@Anywhere plus [1462:6231]
83 -> Terratec Cinergy 250 PCI TV [153b:1160]
84 -> LifeView FlyDVB Trio [5168:0319]
85 -> AverTV DVB-T 777 [1461:2c05,1461:2c05]
86 -> LifeView FlyDVB-T / Genius VideoWonder DVB-T [5168:0301,1489:0301]
87 -> ADS Instant TV Duo Cardbus PTV331 [0331:1421]
88 -> Tevion/KWorld DVB-T 220RF [17de:7201]
89 -> ELSA EX-VISION 700TV [1048:226c]
90 -> Kworld ATSC110 [17de:7350]
91 -> AVerMedia A169 B [1461:7360]
92 -> AVerMedia A169 B1 [1461:6360]
93 -> Medion 7134 Bridge #2 [16be:0005]
94 -> LifeView FlyDVB-T Hybrid Cardbus [5168:3306,5168:3502]
95 -> LifeView FlyVIDEO3000 (NTSC) [5169:0138]
96 -> Medion Md8800 Quadro [16be:0007,16be:0008]
97 -> LifeView FlyDVB-S /Acorp TV134DS [5168:0300,4e42:0300]
98 -> Proteus Pro 2309 [0919:2003]
99 -> AVerMedia TV Hybrid A16AR [1461:2c00]
100 -> Asus Europa2 OEM [1043:4860]
101 -> Pinnacle PCTV 310i [11bd:002f]
102 -> Avermedia AVerTV Studio 507 [1461:9715]
103 -> Compro Videomate DVB-T200A
104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid [0070:6701]
105 -> Terratec Cinergy HT PCMCIA [153b:1172]
106 -> Encore ENLTV [1131:2342,1131:2341,3016:2344]
107 -> Encore ENLTV-FM [1131:230f]
108 -> Terratec Cinergy HT PCI [153b:1175]

************************************************** *********************************

You will also have to select the tuner number from the list of tuners, which can be found in /usr/src/linux/Documentation/video4linux/CARDLIST.tuner or this list below:

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
tuner=42 - Philips 1236D ATSC/NTSC daul in
tuner=43 - Philips NTSC MK3 (FM1236MK3 or FM1236/F)
tuner=44 - Philips 4 in 1 (ATI TV Wonder Pro/Conexant)
tuner=45 - Microtune 4049 FM5
tuner=46 - Panasonic VP27s/ENGE4324D
tuner=47 - LG NTSC (TAPE series)
tuner=48 - Tenna TNF 8831 BGFF)
tuner=49 - Microtune 4042 FI5 ATSC/NTSC dual in
tuner=50 - TCL 2002N
tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)
tuner=52 - Thomson DDT 7610 (ATSC/NTSC)
tuner=53 - Philips FQ1286
tuner=54 - tda8290+75
tuner=55 - TCL 2002MB
tuner=56 - Philips PAL/SECAM multi (FQ1216AME MK4)
tuner=57 - Philips FQ1236A MK4
tuner=58 - Ymec TVision TVF-8531MF/8831MF/8731MF
tuner=59 - Ymec TVision TVF-5533MF
tuner=60 - Thomson DDT 7611 (ATSC/NTSC)
tuner=61 - Tena TNF9533-D/IF/TNF9533-B/DF
tuner=62 - Philips TEA5767HN FM Radio
tuner=63 - Philips FMD1216ME MK3 Hybrid Tuner
tuner=64 - LG TDVS-H062F/TUA6034
tuner=65 - Ymec TVF66T5-B/DFF
tuner=66 - LG NTSC (TALN mini series)
tuner=67 - Philips TD1316 Hybrid Tuner
tuner=68 - Philips TUV1236D ATSC/NTSC dual in
tuner=69 - Tena TNF 5335 MF

---

### Post by merkez3110 on 2011-05-20
[FONT=Lucida Console]my hardware first: saa7134 / alsa650
to run it with tvtime (with sound, etc.)
  
don't forget to "reboot" when you're told so.
  
(1)
insert [/FONT][FONT=Lucida Console]"saa7134"[/FONT][FONT=Lucida Console] at the end of file "/etc/modules"
  
(2)
insert [/FONT][FONT=Lucida Console]"options saa7134 i2c_scan=1 card=81 tuner=54" into [/FONT][FONT=Lucida Console]"/etc/modprobe.d/options" file
  
reboot
  
(3)
$ sudo apt-get install sox libsox-fmt-all tvtime xmltv-util
  
(4)
$ sudo apt-get install tvtime
tv standart > PAL
sound standart > PAL-BG
frequency table > europe
  
(5)
$ lspci | grep SAA
will give output like as follows:
02:03.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
"02:03.0" is the address of the sound system (select yours from your output)
  
(6)
$ LANG=C pactl list | grep -A2 alsa
note all output lines like "alsa_input.pciXXXXXXXXXXXXXXX"
for example:
alsa_input.pci-0000_02_03.0.analog-stereo
alsa_output.pci-0000_00_10.1.analog-stereo.monitor
alsa_input.pci-0000_00_10.1.analog-stereo
select the one with the matching numbers noted in step 5
for example, my selection would be: "alsa_input.pci-0000_02_03.0.analog-stereo"
  
(7)
insert the line
[/FONT][FONT=Lucida Console]"load-module module-loopback source=alsa_input.pci-0000_02_03.0.analog-stereo"
at the end of file [/FONT][FONT=Lucida Console]"/etc/pulse/default.pa"
  
(8)
restart pulse audio
$ pulseaudio -k
  
or better reboot
  
(9)
now correct the line
[/FONT][FONT=Lucida Console]<option name="MixerDevice" value="default/Line"/>[/FONT]
in the file  [FONT=Lucida Console]"/etc/tvtime/tvtime.xml"
like:
<option name="MixerDevice" value="hw:0/PCM"/>
  
reboot.
  
start tvtime (no need to use "sudo", use the gui menu)
  
search the channels and you're done.
  
any questions? [email]merkez3110@gmail.com[/email]
[/FONT]

---


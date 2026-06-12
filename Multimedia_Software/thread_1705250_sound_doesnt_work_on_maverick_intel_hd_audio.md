---
title: "sound doesnt work on maverick intel hd audio"
date: 2011-03-11
forum: Multimedia Software
---

### Post by jewfromdahood on 2011-03-11
I have made a custom kernel a few weeks ago, and just today the sound on everything isn't working. Upgraded alsa to 1.0.24 to try to fix and nothing...  What do I need to do?

---

### Post by jewfromdahood on 2011-03-12
bump

---

### Post by jewfromdahood on 2011-03-12
fixed it!
Under model for snd-hda-intel, I was stumped under which model to specify as I built my laptop from barebones. So I took a shot and put "auto" and voila after a reload of alsa music, has never ever sounded so good to hear. from [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
To use the database, find the make and model of your machine and then open the alsa-base file as root so you can edit it
Code:
sudo gedit /etc/modprobe.d/alsa-base
(If you are using Jaunty the file name has changed to alsa-base.conf to conform to the new configuration file naming convention)

at the end of the file add

Code:
options snd-hda-intel xxx...=xxxx....
replacing the xxxx with the option you found. More than one option may be necessary and can be placed on the same line. You will see examples below. If there is more than one line listed after your machine, use them as listed.

Restart alsa. 
Code:
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
(You also may be able to just log out and log back in but you may need to reboot for the option to be implemented.)

The database is arranged by manufacturer and model. If there is no option listed for your machine you should try the options used for similar machines. Some dell and compaq models have been reported to work with hp options and some hps with toshiba options so you can see how confusing this is getting.

These are options as reported by users so there may be errors. If you have found an option that works better, please let us know. There are also some links at the end for more options and other help with sound.

ACER , options snd-hda-intel model=acer
Aspire 4710, Aspire 5600,Travelmate options snd-hda-intel model=acer
Aspire 9810 model=acer-aspire
5920g,Aspire 8930, model=auto
M50sa-x1 model=haier-w66
Acer Aspire 9815WKMi options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=acer-aspire position_fix=1 enable=yes 
Aspire5536-5883 options snd-hda-intel model=auto(no built in mic)
Aspire 6920G (codec ALC889)
ALSA 1.0.20
options snd-hda-intel model=auto

Advent 6555 (MSI GT725)
options snd-hda-intel probe_mask=1
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
options snd-hda-intel model=targa-dig

Alienware
M9750 model=6stack-dig

ASUS
A7J model= asus-a7j
A7M model=asus-a7m
F2/F3 model= asus-laptop
F6A-2 model=6stack
enable_msi=1
single_cmd=1
G50v model=g50v
G71v model=g71v
H13 model=h13
M2R32-MVP model=6stack
M51SN-AP067G model=lenovo
NV80 model=g50v position_fix=0
X20G, U1E model=lenovo
W2JC model=w2jc
Eeepc P701 model=eeepc-p701
Eeepc-EP20 model=eeepc-ep20

Compaq
Compaq CQ40, CQ71 
options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
Compaq 6735s
options snd-hda-intel model=laptop


Dell model=dell
T3400, Vostro 1200 model=dell
XPS 410 model=dell-bios
Dimension E520 model=dell-3stack
Dimension 9150 model=dell-m81
Inspirion 1420n options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
Adamo
options snd-hda-intel model=dell-eq
Dell M1330, model=dell-3stack
dell vostro 1000 / inspirion 1501 model=dell-m23

1526 model=dell-m81
Inspirion 530 model=6stack-dell
desktops model=dell-m4-1 STAC92HD71B
model=dell-m4-2 STAC92HD71B
model=dell-m6 STAC92HD73
model=dell-bios STAC92HD73
Studio 540 snd_hda_intel probe_mask=1 


Fujitsu model=fujitsu
Pi1536 model= 3stack-dig
Pi2515 model= fujitsu-pi2515
The following needs Alsa 1.0.19 or later
Pi3540 model=fujitsu-xa3530
xa3530

Gateway model=gateway
gt5405e model=gateway
T-1616 model=dell-m42
mx (not all) model=m2-2
nx (not all) model=m6
P-6831FX, 6860-fx
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1

HP model=hp
tx1000, tx2000z model=hp
3013 model=hp-3013
nx6325 model=toshiba
6535b model=laptop
6735s model=laptop enable_msi=1 
TX2635us (tx2500 series) model=toshiba position_fix=1
xw4400/6400, 8400/9400 model=hp-bpc
BPC D7000 model=hp-d7000
Thin Client T5735 model=hp-tc-t5735
dv4-1120us, dv4-1124nr, dv4-1124cl, dv4-1150, dv4-1000ea, dv7 enable_msi=1
dv5 (some), dv4z model=dv5
dv4-1210ef
options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1
dv5 (some)
options snd_slots=snd-hda-intel
options snd-hda-intel enable_msi=1 singel_cmd=1
hptx2510us model=toshiba position_fix=1
or
options snd-hda-intel model=zepto position_fix=1
dv6
options snd-hda-intel model=dell-m4-3 enable_msi=1
dv7t-2000
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
-Upgrade ALSA to 1.0.19
HP dv5 -1235dx l
HP DV3510nr
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
HP dv6 1100.EO
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-dv5
options snd-hda-intel enable_msi=1
HP DV6z 
ALSA 1.0.20 
options snd-hda-intel model=dell-m4 enable_msi=1
HP Pavilion DV 3500 or DV 3000
options snd-hda-intel model=dell-m4-1
hp dv6-1007tx
alsa 1.0.21
options snd_hda_intel model=hp-dv5
HPdv6t-1200
option snd-hda-intel model=dell-m4-1
HP Pavilion DV7-1002tx
ALSA 1.0.21
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1
HPDV7-1125ea
options snd-hda-intel enable_msi=1
(no subwoofer)
Hp Pavilion Dv6-1108sl
alsa 1.0.20
snd-hda-intel model=dell-m4-3 enable_msi=1
(no headphone/ext mic)
HP HDX9300
options snd-hda-intel model=5stack position_fix=0 probe_mask=-1 bdl_pos_adj=-1 enable=yes
(no heaphone jack 1)
HP TouchSmartPC tx2 - 1025dx
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

Lenovo model=lenovo
3000, C200 model=lenovo
101e model=lenovo-101e
3000 N100 model=6stack
MS7195 model=lenovo-ms7195
NB0763 model=lenovo-nb0763
Thinkpad, X300, T60/X60/Z60/T61/X61 model=thinkpad
y410 model=lenovo-3000

LG model =lg
LW20/LW25 model=lg-lw

Mac
iMac (24inch) model=imac24
Macpro model=macpro
Macbook Pro rev3 model=mbp3

MEDION MD 96380 model=lenovo-nb0763 

MSI
M662 model=targa-dig
model=targa-2ch-dig

Packard Bell
Easynote model=3stack
See post #4

Samsung model=laptop
M50 model=laptop
R65 model=laptop-eapd
Ultra tablet pc model=ultra

Sony model=sony
Vaio model=sony
VGN-FZ35M, VGN-SZ750N, S460N/C model=vaio
Vaio VGN-CS360A, model=toshiba-s06


Toshiba model=toshiba
A200 model=lenovo
A205, Tecra A10, U205 model=toshiba 
A135-S4577 model=3stack (no mic/spkr switch)
L30-106 model=dallas
L35-S2174 model=6stack-digout
Satellite A100-192 model=3stack

---


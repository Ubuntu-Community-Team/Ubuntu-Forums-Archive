---
title: "BTTV Capture card"
date: 2008-10-05
forum: Multimedia Software
---

### Post by tsumaru on 2008-10-05
Hi there, 

I have a BTTV based 4 port capture card. Unfotunately in lspci it doesnt give me a model.. just 
03:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
03:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

After spending a few hours on BTTV Gallery i have found my card is apparently a TE104B.

The problem is i am unsure as to which card= setting to use in modprobe options. when i currently try to record something using mencoder (or even to view it with tvtime) all i get is a blue screen. 

This is something thats been bugging me for a few weeks now.. can anyone help me or at least point me in the right direction?

dmesg:

[ 3317.266405] bttv0: Bt878 (rev 17) at 0000:03:00.0, irq: 20, latency: 64, mmio: 0xd2000000
[ 3317.267353] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[ 3317.267409] bttv0: gpio: en=00000000, out=00000000 in=00f360ff [init]
[ 3330.047488] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[ 3330.047500] bttv0: tuner type unset
[ 3330.047506] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[ 3336.437368] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[ 3342.827241] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 3349.217208] bttv0: registered device video0
[ 3349.217471] bttv0: registered device vbi0

---

### Post by xc3RnbFO8P on 2008-10-05
Try **lspci -vn** in terminal.
Check this:
[http://ubuntuforums.org/showthread.php?t=621437]("http://ubuntuforums.org/showthread.php?t=621437")
[http://www.linuxtv.org/v4lwiki/index.php/AVerMedia_TVCapture_98]("http://www.linuxtv.org/v4lwiki/index.php/AVerMedia_TVCapture_98")
Read this:
[https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091272.html]("https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091272.html")

---

### Post by tsumaru on 2008-10-05
03:00.0 0400: 109e:036e (rev 11)
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at d2000000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

03:00.1 0480: 109e:0878 (rev 11)
        Flags: medium devsel, IRQ 20
        Memory at d2001000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
^^ lspci -vn

even though my card is not the same as the one in the link i tried card=13 to no avail i still get a blue screen

---

### Post by xc3RnbFO8P on 2008-10-05
What do you get when you run **dmesg** in terminal?

---

### Post by tsumaru on 2008-10-05
dmesg output is in the first post

---

### Post by xc3RnbFO8P on 2008-10-05
> even though my card is not the same as the one in the link i tried card=13 to no avail i still get a blue screen

dmesg should show:
> bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004


Check **sudo gedit /etc/modules**
is there something like this:
> > lp
> psmouse
[B]> bttv
> bt878[/B]

if you dont have bttv and bt878, add it.
Restart the computer and do dmesg again and try tvtime.

---

### Post by tsumaru on 2008-10-06
dmesg does indeed show that, along with insmod,options in it too.

both modules bttv and bt878 are loaded in modules and when the computer boots up. i have even tried adding bttv card=13 into /etc/modprobe.d/options.

When i load tvtime (or mencoder) all i get is a blue screen.

Tvtime, with card=13 only shows TV, Composite1 and Svideo whereas if i leave it to autodetect it gives me TV, Composite1, Svideo and Composite3  

I have tried something on each port under each of the settings in tvtime. blue screen.

As you can see, this has been bugging me a while :)

---

### Post by xc3RnbFO8P on 2008-10-07
You can try:
unload bttv and tuner using "**rmmod bttv**" and "**rmmod** tuner".
Then:
> modprobe bttv card=13 tuner=2

---

### Post by tsumaru on 2008-10-25
sorry it has taken me so long to reply, i have been having problems with my internet.

Right, using card13 and tuner2 i can now get a picture.

Input 0 and 1 are both colour however input 2 is black and white
also the last input for the card isnt being mapped anywhere


Do you know of a way i can get the last 2 to display colour also?

And on an unrelated note to this, is there any way i can capture all four cameras at the same time?

---

### Post by xc3RnbFO8P on 2008-10-25
Try more **PAL** tuners

```
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
```

---

### Post by secs on 2008-11-25
Hi all.

Googling for a solution to basicaly the same symptoms, I came across this site and these posts. I have basically no hair left from playing.

I have a 4 port capture card based on a bt878 chip. It has no audio input jack and no tuner. Doing a Dmesg I get

Bt878 (rev 17)    ***UNKNOWN/GENERIC *** [card=0, autodetected]

Tuner type unset


with bits and pieces of other info

then a line that says bt878_probe: card id=[0xffffffff], Unknown card
exiting.


So is it possible I can use the info above

like

You can try:
unload bttv and tuner using "rmmod bttv" and "rmmod tuner".
Then:
Quote:
modprobe bttv card=13 tuner=2 

and simply keep going changing numbers till it works?


So far the best I have done is get a blue screen with no camera's connected and then if I plug a camera in, I get grey sort of picture that looks like a black and white tv not tunes into a channel correctly. Yeah I am old enough to know what a black and white tv is :-)

As mentioned above, this seems to be the best info I have found to date.

Thanks

---


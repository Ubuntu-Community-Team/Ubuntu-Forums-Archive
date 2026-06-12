---
title: "no sound after update"
date: 2010-05-08
forum: Multimedia Software
---

### Post by The End of The World on 2010-05-08
hey
[yeah i checked to see any solutions...tried and couldnt find any that worked]

ok so a while ago i updated ubuntu and the sound stopped working. i cant hear anything now not even a system beep - i tried  	 	the Comprehensive Sound Problem Solutions Guide by LordRaiden but to no success. i tried alsamixer and all that to check its muted, and its not

any help would be greatly welcomed :p

 		 		 			 				 					 					 					 					 					 [ ]("http://ubuntuforums.org/forumdisplay.php?f=334#")

---

### Post by lidex on 2010-05-08
So you already had working lucid install and a recent update broke your sound? Is that correct?

Had you done any tweaking previously to get sound working such as an alsa upgrade? (That would be overwritten by a new kernel)

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by The End of The World on 2010-05-09
uname -a returned as this;
Linux dell-latitude 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

aplay -l returned;
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version gave;
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#* gave;
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa

yep i wasnt very inventive with my computer name =P
thanks for such a fast response =]

==edit==
my headphones work...weirdly

---

### Post by The End of The World on 2010-05-09
oh, never mind, i was putting ubuntu studio on the computer (which didnt work), and exited and it suddenly started working :) weird though - could be a possible bug?

---


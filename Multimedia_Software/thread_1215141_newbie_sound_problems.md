---
title: "newbie sound problems"
date: 2009-07-16
forum: Multimedia Software
---

### Post by -limp- on 2009-07-16
hello i am new to ubuntu and linux in general

system sound seams to work now that i went from alsa to oss but no online or media sounds work
my card is a creative sound blaster audigy

when i go to system-preferences-sound i have it set to audigy ca0106 and test works but when i click on my sound icon and go to volume control the only ca0106 listed is pulseaudio

so i searched and typed in alsa -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
so it seems like it recognizes it to me
i am almost positive nothing is muted  and any help wold be greatly appreciated

---

### Post by enz1m3 on 2009-07-18
When you right-click -> Open Volume Control what devices do you see? And in the appropriate device, make sure to show ALL items because sometimes there are some "Aux" or "controllers" that are muted and influentiate certain applications.

---

### Post by igorzwx on 2009-07-18
aplay would not find anything if you have OSS4

try 

osstest

read pdf documetation, 
it is very small 1 page

---


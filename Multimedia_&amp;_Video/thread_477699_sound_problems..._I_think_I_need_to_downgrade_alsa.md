---
title: "sound problems... I think I need to downgrade alsa"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by joeally on 2007-06-18
Well my sound was working perfectly i was happy as can be with beryl etc. Then I was trying to get my microphone to work. So I installed the latest ALSA drivers from source. 

Thats where everything went wrong. Sound stopped working. 

So being pissed off I re-installed off the feisty cd (well Linux mint cassandra but they are basically the same). But sound still doesn't work.

So i was wondering maybe before i installed off source my alsa drivers were pretty old, cuz on my new install alsa doesnt work. 

when I type alsamixer into the terminal it lets me control all the sound levels, except headphones. My speakers are connected to the headphones slot is this normal? What is PCM?
 
Do I need to downgrade?

How do I downgrade?

```
joe@joe-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---


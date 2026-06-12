---
title: "Sound and Video Playback Problem"
date: 2009-09-06
forum: Multimedia Software
---

### Post by MadDawg010 on 2009-09-06
Alright, I having a very annoying problem with my sound and video playback. After random amounts of time, any video I may be watching slows down to about 1 frame every 15 seconds and anything else that uses sound becomes unresponsive or otherwise unusable. Also, the sound loops the last few milliseconds of whatever was playing indefinitely, and I have to mute the sound in order to give my ears a rest. 

Sometimes I get lucky and I can use any multimedia app for around 30 minutes, but most of the time I get about 15 seconds or even no time at all, because the boot-up sound loops. This usually happens when I immediately switch from XP to Ubuntu, but if I let the RAM flush out, I get the usual 15 seconds.

Specs (most relevant)

ThinkPad R51e
SoundMAX Integrated Digital Audio (According to XP)
ThinkPad Integrated 56K Modem (According to XP)
Ubuntu 9.04, latest kernel

Tying "aplay -l" gives me these devices:
> **** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any suggestions?

---

### Post by MadDawg010 on 2009-09-07
Bump

---

### Post by MadDawg010 on 2009-09-07
Alright, I think I fixed it. I just followed the guide here: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

Thanks for at least looking at this thread.

---


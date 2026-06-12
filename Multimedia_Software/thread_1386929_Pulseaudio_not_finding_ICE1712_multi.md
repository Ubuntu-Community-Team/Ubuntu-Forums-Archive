---
title: "Pulseaudio not finding ICE1712 multi"
date: 2010-01-21
forum: Multimedia Software
---

### Post by garethyoung on 2010-01-21
Hi, I've recently upgraded to 9.10 and have lost all sound :(

It seems from the forums that this is happening a lot. However, I have not been able to get any of the fixes to work for me. I've had sound issues before and resolved them with earlier versions of ubuntu but this one's a doozie.

This is my aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: DMX6Fire [TerraTec DMX6Fire], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So the card is there,

but when I go to pulseaudio it is not an option for selection in the output devices. I have concluded that this is a pulseaudio problem because the sound card appears in the GNOME ALSA Mixer.

Can anyone offer some hints or a walk through that would suit my issue? (I'm still relatively new at this, so go easy on me)

---


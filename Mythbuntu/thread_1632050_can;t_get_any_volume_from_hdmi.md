---
title: "can;t get any volume from hdmi"
date: 2010-11-27
forum: Mythbuntu
---

### Post by lime4x4 on 2010-11-27
under alsa mixer i can't adjust the volume it shows up as 00. When highlited i tried using the up arrow button to increase the volume but it doesn't change.

---

### Post by nickrout on 2010-11-28
> **lime4x4 said:**
> under alsa mixer i can't adjust the volume it shows up as 00. When highlited i tried using the up arrow button to increase the volume but it doesn't change.


that's correct. you can't change the volume on a digital stream without decoding and re-encoding the stream. Use the vol control on your amp/tv.

---

### Post by lime4x4 on 2010-11-28
Well that's the problem i have no sound coming thru the tv over hdmi.I guess it's time to gig deeper into this

---

### Post by Xrcam on 2010-11-28
Got this problem a couple of weeks ago.
 
Put all volumes to maximum.
Ensure alsamixer shows 00 (not MM) under hdmi sliders.
 
Put this line at the end of /etc/modprobe.d/alsa-base
options snd-hda-intel model=3stack
 
Configure audio output in mythfrontend to hdmi. You could have multiple setup to try.
 
 
This is what i've done to get sounds thru hdmi.

---

### Post by nickrout on 2010-11-28
have you scanned for audio devices? (in mythtv, settings, general).

---

### Post by lime4x4 on 2010-11-28
I've tried all settings and some work arounds found on this forum but still no joy.. The hardware is detected thou

john@john-MCP73:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by nickrout on 2010-11-28
have you scanned for audio devices? (in mythtv, settings, general).

---

### Post by byronmyth on 2010-11-29
Load up alsamixer, press F6 and select the Nvidia, do you see the inputs listed? If not you may need to load a alsa backport (look for my other post).

---


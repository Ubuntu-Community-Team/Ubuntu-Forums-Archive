---
title: "HDMI Audio - 1/2 Working..."
date: 2008-11-16
forum: Multimedia Software
---

### Post by cmckee1980 on 2008-11-16
Hello,

After a day of messing around with settings and drivers and downloads galore, I have managed to produce some sound through my HDMI cable.  Rhythmbox and playing DVD's work great but I cannot seem to get Firefox (like CNN videos, etc...) to work. I can do the "test"s in the System-> Prefs -> Sound and I've it selected to "HDA ATI HDMI ATI HDMI (ALSA)".  

Any ideas?  Thank you...

Here is some output from my aplay:

ME@MY-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---


---
title: "Cannot select front headphone as audio output"
date: 2008-07-17
forum: Multimedia Software
---

### Post by bogdanbiv on 2008-07-17
I have one onboard sound card with 2 audio exits:
[LIST]
[*]one the back of the computer (with several sound channels/jacks)
[*]one on the front of the PC for the microphone & headphones
[/LIST]

Front mic works perfectly, but the headphones do not as the output remains on the speakers in the back. That alone is not very annoying in  itself, but it has the side effect of producing a high pitch sound (when the microphone picks up the sound in the speakers amplifying it until it becomes unbearable).

Also I find it peculiar that in alsamixer I'm shown a headphone channel but it's at 00 and I can't modify it. In kmixer I don't see any headphone channel.

Any ideas how should I use the front headphone jack + mic without removing the speakers jack from the back?


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm using Kubuntu 8.04 32bit
$ uname -a
Linux bog-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---


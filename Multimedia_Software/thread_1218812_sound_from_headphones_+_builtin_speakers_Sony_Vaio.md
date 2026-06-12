---
title: "sound from headphones + builtin speakers Sony Vaio 9.04"
date: 2009-07-21
forum: Multimedia Software
---

### Post by hasana on 2009-07-21
Hello,
I'm using Ubuntu 9.04 with all recent patches. Up to about a week ago when I plugged in my headphones into my Sony Vaio VGN-NR21Z I got sound only through the headphones. Now I get sound through both headphones and the builtin speakers. I'm not sure why.

I'm not using pulseaudio (have removed it) since I had problems when using Skype.

Running aplay -l gives me:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I had things working up to about a week ago with the following line in my alsa-base:

options snd-hda-intel model=sony-assamd

I believe that there was a sound patch that I installed, but I can't figure out why I'm now getting sound through the speakers and the headphones. If I could figure out how to turn down/off the builtin speakers without affecting the headset that would do just as well.

Anyone hit this problem recently?
adil

---

### Post by igorzwx on 2009-07-21
many have similar problems.
if your headphones are not a USB thing,
you may try OSS4.
USB audio devices are not supported by OSS4

see OSS (Open Sound System) in Wikipedia

---


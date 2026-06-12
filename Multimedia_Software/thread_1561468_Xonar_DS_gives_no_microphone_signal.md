---
title: "Xonar DS gives no microphone signal"
date: 2010-08-26
forum: Multimedia Software
---

### Post by chronozphere on 2010-08-26
Hey,

I previously had the SB Audigy SE, which worked but couldn't record. Now I bought the Xonar DS and I still have the same problem (allthough playback quality is 5x better). 

I'll explain everything step by step:

> I plugged the red plug (mic) of my headset into the red socket of my card.
> I've upgraded to ALSA 1.0.23 with the great ALSA upgrade script available on these forums (big thanks for that :D ). This made my soundcard work.
> I played with alsamixer (pictures included)
> I made sure that the mic was not muted and that the volume was all the way up.
> I've taken a look at gnome-alsamixer, but it didn't help me (yet).
> I have NOT take a look at .asoundrc. Can this config help me fix my mic?
> again, Audio playback works flawlessly since the 1.0.23 upgrade.

I've tested multiple times with arecord/aplay, audacity and gnome sound recorder, but it never worked. If I turn the speakers all the way up, I only get some noise.

I'm running ubuntu 9.10.

Heres the output from "amixer":

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 135 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB] [on]
  Front Right: Playback 255 [100%] [0.00dB] [on]
  Rear Left: Playback 255 [100%] [0.00dB] [on]
  Rear Right: Playback 255 [100%] [0.00dB] [on]
  Front Center: Playback 255 [100%] [0.00dB] [on]
  Woofer: Playback 255 [100%] [0.00dB] [on]
  Side Left: Playback 255 [100%] [0.00dB] [on]
  Side Right: Playback 255 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 61 - 127
  Mono:
  Front Left: Playback 127 [100%] [on]
  Front Right: Playback 127 [100%] [on]
Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Aux',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'ADC Filter',0
  Capabilities: cenum
  Items: 'None' 'High-pass Filter'
  Item0: 'High-pass Filter'
Simple mixer control 'Analog Input Monitor',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 1
  Mono: Playback 1 [100%] [0.00dB] [on]
Simple mixer control 'Input',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 165 - 255
  Front Left: Capture 255 [100%]
  Front Right: Capture 255 [100%]
Simple mixer control 'Level Control',0
  Capabilities: cenum
  Items: 'None' 'Peak Limiter' 'Automatic Level Control'
  Item0: 'None'
Simple mixer control 'Noise Gate',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Stereo Upmixing',0
  Capabilities: enum
  Items: 'Front' 'Front+Surround' 'Front+Surround+Back'
  Item0: 'Front+Surround+Back'

```And some pictures:

_[[IMG]http://a.imageshack.us/img801/1548/screenshotsoundpreferen.th.png[/IMG]](http://img801.imageshack.us/i/screenshotsoundpreferen.png/)_

[[IMG]http://a.imageshack.us/img844/2406/playback.th.png[/IMG]]("http://img844.imageshack.us/i/playback.png/")

[[IMG]http://a.imageshack.us/img826/9928/recordr.th.png[/IMG]]("http://img826.imageshack.us/i/recordr.png/")

I believe the driver developer for the Xonar driver said that it was 98% complete. Also he stated that "some inputs" didn't work yet (on the alsa compatibilty matrix). So I assume that basic mic recording should be possible. If not, can someone please recommend me a card that WILL record in Ubuntu 9.10?

Can anybody help me? :(

Thanks a bunch. :)

---

### Post by chronozphere on 2010-08-27
Ok, epic fail on my side. #-o

I misinterpreted the picture of the PCI card in the manual. I plugged the mic in the left-most hole, while it should've been the right-most one (as seen from the back). The left-most hole had a red LED in it, so I was assuming it was meant for the mic. NOT! *smashes head against wall*

Recording works now. arecord gives me crappy recordings but that's probably because I dont use the right options. Audacity and Gnome sound recorder work great.

Edit: I also made another mistake. I thought the DS had leds for all holes (like the D2 has), but it only has one for the left-most because that must be an optical connection or something.

---


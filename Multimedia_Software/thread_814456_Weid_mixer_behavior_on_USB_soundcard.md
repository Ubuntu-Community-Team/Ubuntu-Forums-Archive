---
title: "Weid mixer behavior on USB soundcard"
date: 2008-05-31
forum: Multimedia Software
---

### Post by ebike on 2008-05-31
Hi All,

I found a cheap USB stereo only soundcard on-line and thought i'd try it out. It actually sounds quite good, but I am having issues with the mixer for it.

I am using it on my Mythtv system temporarily until I get better support for my Creative X-Fi Xmod USb card.

The problem is that I cannot get Mythtv to adjust the mixer for this car either under OSS or ALSA.

Firstly under OSS:
Using the command line amixer command, it DOES work with OSS, i.e the following works and sets the volume: (using /dev/dsp1 and /dev/mixer1 devices in Mythtv setup playing some music)

>  amixer -c 1 set PCM 3000
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 17152
  Mono:
  Front Left: Playback 3000 [17%] [0.00dB] [on]
  Front Right: Playback 3000 [17%] [0.00dB] [on]

Alsamixer does not work

Now with ALSA:

I set the default card to the name of my card that shows up with "asoundconf list" it shows up as "default"

In Mythtv I set both the sound device and the mixer to use ALSA:default
still no mixer action, and amixer doesn't adjust the volume where it would with OSS emulation.

Can anyone give any suggestions what to try next?

As a last resort /hack/ I could write a script that calls amixer and link it to the volume buttons on my remote, but I would rather it worked.

Thanks

---

### Post by ebike on 2008-05-31
Ok, I was mistaken with amixer working for OSS, all it does is if you lower the volume enough it mutes the audio, same as alsamixer.
Anyone?

---


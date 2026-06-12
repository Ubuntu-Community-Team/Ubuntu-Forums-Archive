---
title: "SPDIF/IEC958 Digital Audio Output - No Sound"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by sergiom1973 on 2008-01-29
The short story is that I can't the digital audio output working on my laptop.

I have Gutsy running on my Dell Inspiron 640m laptop.  According to the manual there is a digital audio output which comes out the 7-pin SPDIF connector.  I have an adapter (DP/N 044CTV) connects to the port and provides RCA plug for digital output.  I have a cable connected from the digital out to the digital in on my A/V receiver.

I ran the speaker-test tool to check to if the connection was working.  I didn't get any errors, but I also didn't hear any sound.

```

$ speaker-test -c2 -Dhw:0,1

speaker-test 1.0.15

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right

```

Here is some alsa information:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [-9.00dB] [on]
  Front Right: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic'
  Item0: 'Mic'

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Jan 27 2008 for kernel 2.6.22-14-generic (SMP).

```

I read several posts about similar issues and there was a suggestion upgrade to alsa 1.0.15.  I did that and I didn't see any difference.

Does anyone have suggestions on how to debug this?

Thanks,
Sergio

---

### Post by laasworld on 2008-04-05
I, too, feel your pain..

Though I am running Debian Etch, I am running Alsa 1.0.16rc2 and all the relevant information about it can be found at [http://pastebin.ca/973383](http://pastebin.ca/973383).

I have purchased a dongle (7-pin s-video --> composite video/SPDIF digital audio/4-pin s-video @ [http://www.svideo.com/7pinwspdif.html](http://www.svideo.com/7pinwspdif.html)) but I'm still having no luck.

Windows Vista drivers definitely do not support this capability but surely Linux shouldn't have the same problem? I have yet to find somebody that's gotten everything to work. At one point I found a post that claims one has to be connected through composite video to get the audio to work as well.

What's the deal?!? Anybody? Pleeeease? :confused:

---

### Post by warp99 on 2008-04-05
The mixer sees the IEC958 port:

> Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

Are the level turned down? Go into alsamixer and turn the level all the way up.

---

### Post by markc on 2008-06-25
I have the same problem, Gutsy, alsa 1.0.15, Dell 640m using the yellow RCA from the SPDIF connector (presumably the RGB ones are for composite). I have confirmed that the RCA cable and my output gear works okay with a Creative card so the only thing I have not tried yet is to use the RGB component into a monitor and see if that kicks the digital audio into life.

---


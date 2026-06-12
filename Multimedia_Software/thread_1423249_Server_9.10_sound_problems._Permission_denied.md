---
title: "Server 9.10 sound problems. Permission denied?"
date: 2010-03-06
forum: Multimedia Software
---

### Post by Thallid on 2010-03-06
Hi!

I've got a fresh installed Ubuntu Server 9.10 system and I'm having problems with the sound. I have two soundcards, ESI Juli@ and Intel HDMI. Here it goes:

```

$ aplay -l
aplay: device_list:223: no soundcards fund...
```


```
$ speaker-test

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Playback open error: -13,Permission denied
Playback open error: -13,Permission denied
Playback open error: -13,Permission denied
```

```
$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

**When I su and change to root access it's a bit different:**

```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Juli [ESI Juli@], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Juli [ESI Juli@], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
# speaker-test -D plughw:1,0 

speaker-test 1.0.20

Playback device is plughw:1,0
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 16 to 32768
Period size range from 8 to 16384
Using max buffer size 32768
Periods = 4
was set period_size = 8192
was set buffer_size = 32768
 0 - Front Left
Time per period = 2.219547
 0 - Front Left
Time per period = 2.901288
 0 - Front Left
```

And a nice noise is coming from my speakers. However, I have to define what card and device to use, without it I get this: 
```
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
Playback open error: -2,No such file or directory
```

```
# alsamixer -c 1

(here comes the alsamixer for my ESI Juli@)
```

Youtube and xmms2 won't play anything through my ESI-card, but both have been started from my user and not from root, maybe that's the problem?

So, what's wrong and how do I fix it? :p

---

### Post by Thallid on 2010-03-06
Bump.

I've done some further testing. First I thought maybe there was something special with the server version, so I tried my luck with Ubuntu Minimal. Same things installed, alsa-base, alsa-utils but "Permission denied" when I ran speaker-test. I also tried Ubuntu 10.04 but the result was just the same.

Seriously guys, what could be wrong? ESI Juli@ should work without complication and IT IS! But not when I'm running it as a regular user.

Really need some help here. Tomorrow I'm gonna try Debian Squeeze. Last on my list: Windows, but I don't want to go there.

---


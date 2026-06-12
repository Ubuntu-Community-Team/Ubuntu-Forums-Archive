---
title: "No ALSA capture on my USB card"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by cbrunet on 2006-11-09
Hi!

I have a Edirol UA-3 USB sound card. I'm trying to use it on my iBook (PPC) running Ubuntu Edgy Eft. The card seems to be recognized, and I can play sound through it. But I'm not able to use the sound input.

In alsamixer, I only see one PCM playback, and no capture at all (I talk about the USB sound card off course, since the internal DACA has no inputs).

The only way I succeed using the input was with JACK, using plughw:1,0 as input instead of hw:0,1 .

```
$ more /proc/asound/cards
0 [DACA           ]: PMac DACA - PowerMac DACA
                     PowerMac DACA (Dev 6) Sub-frame 0
1 [Device         ]: USB-Audio - UA-3 USB Audio Device
                     Roland UA-3 USB Audio Device at usb-0001:10:18.0-1, full speed
$ more /proc/asound/devices
 16: [0- 0]: digital audio playback
  0: [0- 0]: ctl
 33:       : timer
 48: [1- 0]: digital audio playback
 56: [1- 0]: digital audio capture
 32: [1- 0]: ctl
$ more /proc/asound/timers
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P1-0-0: PCM playback 1-0-0 : SLAVE
P1-0-1: PCM capture 1-0-1 : SLAVE
$ more /proc/asound/pcm
00-00: PMac DACA : PowerMac DACA : playback 1
01-00: USB Audio : USB Audio : playback 1 : capture 1
```

Can somebody help me?

---


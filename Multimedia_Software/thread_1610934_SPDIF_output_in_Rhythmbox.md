---
title: "S/PDIF output in Rhythmbox"
date: 2010-11-01
forum: Multimedia Software
---

### Post by peterhaagerup on 2010-11-01
Hi

I am trying to get Rhythmbox output through my S/PDIF output on my sound card. That is pretty straight forward, but there is two problems:

1. The volume can be adjusted in Gnome and Rhythmbox on the digital output which should not be possible - I want 100% clear direct S/PDIF with no sound manipulation, filters or anything like that.

2. Sample rate on the S/PDIF output is always 44.1 kHz, even when playing 48 kHz or 96 kHz material.

I am able to make a direct output to S/PDIF using aplay:
```

aplay -D hw:0,1 file.wav
```

or gstreamer:

```
gst-launch-0.10 filesrc location=file.wav ! wavparse ! alsasink
```

Both these commands do exactly what I want : Pure output (full volume - the volume controls in Gnome have no effect at all) and the output sample rate is true to the sample rate in the file being played.

How can I setup Rhythmbox to output S/PDIF in the same way? I want to be sure that the output is as pure as it can get and be able to play 48kHz and 96kHz files as well. I know that Rhythmbox uses gstreamer, so it should be possible.

---

### Post by roberto.pierpaoli on 2011-04-23
Hi Peter,
I'm looking exactly for the same feature, except that I do not need to use necessarily Rythmbox, also VLC or Banshee would be ok for me, anyway I did not find an answer yet...
Have you been luckier? :)
In case, please share your knowledge!


Roberto

---

### Post by wjamoore on 2011-09-21
Anybody figured out how to play 96khz or 192khz files on linux?

wjam

---

### Post by RR123RR on 2011-12-05
Hopefully a quicker fix than reinventing the whole sound chain like this:
[http://www.lacocina.nl/artikelen/free-and-bitperfect](http://www.lacocina.nl/artikelen/free-and-bitperfect)

Anyone made any progress? :)

---

### Post by BicyclerBoy on 2011-12-05
AFAIK 192KHz/24 over S/PDIF is not commonly supported in consumer audio equipment.

I play all audio (stereo) re-sampled to 96KHz/24bit including 192KHz/24bit because this is the max the AVR will accept.
I use alsa libsamplerate plugin, this is very CPU intensive.
Arguably should be using 88K2Hz.

Pulse audio can be configured to use high quality resampling, the default is budget.

Amarok/clementine allow you to easily point them at an alsa plug.
Clememtine **will** play bit true 192KHz/24bit music.
Rhythmbox may not.
Any player that uses default gstreamer pulse sound system probably can not.

HDMI audio makes it trivial to get bit perfect or HQ resampled & in multi-channel as well.
But you still need a player that does not downsample..(Clementine)
I would think VLC would not downsample but doesn't make a good music app.

---


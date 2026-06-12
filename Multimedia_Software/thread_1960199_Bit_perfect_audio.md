---
title: "Bit perfect audio"
date: 2012-04-16
forum: Multimedia Software
---

### Post by s3MA00RRNY on 2012-04-16
I'm currently obsessing over having bit perfect audio on my setup. I'm trying to figure out what volume to use to achieve this. I have a PCM2706 sound card, and amixer says this when I set the volume to 100%:

```
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 128
  Mono:
  Front Left: Playback 128 [100%] [0dB] [on]
  Front Right: Playback 128 [100%] [0dB] [on]

```When I set the volume to step 100 (not percent 100), it says this:

```
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 128
  Mono:
  Front Left: Playback 100 [78%] [-28.00dB] [on]
  Front Right: Playback 100 [78%] [-28.00dB] [on]

```Which one is the bit perfect maximum (or maybe it's something different)? I know some cards have the ability to go above 100%, and I'm not sure if ALSA's "100%" is the true 100%, or if it's above it.

Edit: I forgot to mention, the graphical slider for the volume goes to about 30% when I set the volume to step 100. Very confusing.

---

### Post by ridetheteapot on 2012-04-17
well, unless i'm totally mistaken --- the volume 'step' is how much the volume will change each time its asked - in the first case the step would be like .78, and just a guess, but the graphical version is like x2 the resolution .39 (makes it more like 40% rather then 30% though, so i could be wrong).
what software are you using to change volume?

anyway - i would think that if you played back at 100% vol, at the same sample rate as source you'd be as bit perfect as possible. (better yet) if your playing through a stereo that supports it use iec (w/ correct sample rate) to really get perfect (no software volume control, only your illmatic stereo decoding).

---

### Post by whell on 2012-04-18
Passing bit perfect audio through Linux has less to do with volume settings (a setting of 100% is fine) and much more to do with selecting the right software and configuring it correctly.  What playback software are you using?  If using Ubuntu or one of its many variants, have you set it to bypass Pulse Audio?

---


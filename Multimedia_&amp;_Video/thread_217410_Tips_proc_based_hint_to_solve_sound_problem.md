---
title: "Tips: /proc based hint to solve sound problem"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by swamytk on 2006-07-17
Beware! Target of this post: People who don't look at /proc (pseudo file system) for troubleshooting purpose.

Yesterday when I was working with Gentoo Linux, I had audio problem. My card was identified properly and driver loaded. But No Sound. There is no */dev/sound/dsp and /dev/sound/mixer[I]. I traced and found that there is a [I]/proc/asound/oss/sndstat* file which lists the status of audio in the machine. It was some thing like this.

> Installed drivers:
Type 10: ALSA emulation

Card config:
Ensoniq AudioPCI ES1371 at 0x9800, irq 9
C-Media PCI CM8738 (model 37) at 0xa400, irq 9

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371
1: MPU-401 (UART)

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG


From the above I came to know that there are no audio and mixer modules loaded. Then I checked the config file of running kernel and identified the related modules (snd_pcm_oss and snd_mixer_oss if i am not wrong). Then I added these modules to /etc/modules.d to load automatically. Works perfectly.

Thought of sharing this info to Ubuntu users too, so that any rare case of such problems in Ubuntu can be solved.

---


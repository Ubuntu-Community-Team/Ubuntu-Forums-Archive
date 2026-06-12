---
title: "ALSA Problem: snd_pcm_delay() returned a value that is exceptionally large"
date: 2010-05-03
forum: Multimedia Software
---

### Post by zfranciscus on 2010-05-03
Hi,

I found a problem with my ALSA.This problem has been registered in launchpad : [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/374010](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/374010)

I have been having this problem since Jaunty.I am using lucid lynx at the moment, and I am wondering whether there is any fix for lucid. 

Full Log Trace:
```

May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c: Its setup is:
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   stream       : PLAYBACK
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   access       : MMAP_INTERLEAVED
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   format       : S16_LE
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   subformat    : STD
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   channels     : 2
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   rate         : 44100
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   exact rate   : 44100 (44100/1)
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   msbits       : 16
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   buffer_size  : 88192
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   period_size  : 44096
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   period_time  : 999909
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   tstamp_mode  : ENABLE
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   period_step  : 1
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   avail_min    : 85988
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   period_event : 0
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   start_threshold  : -1
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   stop_threshold   : 1444937728
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   silence_threshold: 0
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   silence_size : 0
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   boundary     : 1444937728
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   appl_ptr     : 1247467013
May  3 05:16:53 sleeper-laptop pulseaudio[1763]: alsa-util.c:   hw_ptr       : 1250297985
May  3 05:17:05 sleeper-laptop pulseaudio[1763]: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -12123948 bytes (-68729 ms).
May  3 05:17:05 sleeper-laptop pulseaudio[1763]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.

```

---


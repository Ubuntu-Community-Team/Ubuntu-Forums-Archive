---
title: "Sometimes no sound"
date: 2011-01-23
forum: Multimedia Software
---

### Post by zimio on 2011-01-23
From time to time the sound on my laptop just stops working and I have restart the computer to get it working again.

I have Ubuntu Maverick, running on a DELL INSPIRON 1545.

Heres the alsa log,  /var/log/user.log:

```
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 24.
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: snd_pcm_dump():
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: Soft volume PCM
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: Control: PCM Playback Volume
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: min_dB: -51
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: max_dB: 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: resolution: 256
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: Its setup is:
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   stream       : CAPTURE
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   access       : MMAP_INTERLEAVED
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   format       : S16_LE
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   subformat    : STD
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   channels     : 2
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   rate         : 44100
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   exact rate   : 44100 (44100/1)
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   msbits       : 16
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   buffer_size  : 88192
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_size  : 44096
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_time  : 999909
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   tstamp_mode  : ENABLE
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_step  : 1
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   avail_min    : 87310
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_event : 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   start_threshold  : -1
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   stop_threshold   : 1444937728
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   silence_threshold: 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   silence_size : 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   boundary     : 1444937728
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c: Its setup is:
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   stream       : CAPTURE
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   access       : MMAP_INTERLEAVED
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   format       : S16_LE
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   subformat    : STD
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   channels     : 2
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   rate         : 44100
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   exact rate   : 44100 (44100/1)
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   msbits       : 16
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   buffer_size  : 88192
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_size  : 44096
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_time  : 999909
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   tstamp_mode  : ENABLE
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_step  : 1
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   avail_min    : 87310
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   period_event : 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   start_threshold  : -1
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   stop_threshold   : 1444937728
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   silence_threshold: 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   silence_size : 0
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   boundary     : 1444937728
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   appl_ptr     : 87336
Jan 23 15:01:26 zimio-laptop pulseaudio[1585]: alsa-util.c:   hw_ptr       : 87336
Jan 23 16:06:19 zimio-laptop pulseaudio[1585]: ratelimit.c: 1069 events suppressed
Jan 23 18:25:22 zimio-laptop pulseaudio[1585]: ratelimit.c: 612 events suppressed
```

---


---
title: "JACK realtime once again"
date: 2020-05-09
forum: Multimedia Software
---

### Post by 0x656b694d on 2020-05-09
Hello,

I've got Ubuntu 20.04 (5.4.0-29-generic, x86_64), and my user is in the audio group. The RT priority limits look to be set up:
```

$ ulimit -r -l
real-time priority              (-r) 95
max locked memory       (kbytes, -l) unlimited
```

The problem is that jack still cannot start with real-time scheduling:
```

Sat May  9 19:19:07 2020: Starting jack server...
Sat May  9 19:19:07 2020: JACK server starting in realtime mode with priority 10
Sat May  9 19:19:07 2020: self-connect-mode is "Don't restrict self connect requests"
Sat May  9 19:19:07 2020: Acquired audio card Audio1
Sat May  9 19:19:07 2020: creating alsa driver ... hw:USB|hw:USB|512|2|48000|0|0|nomon|swmeter|-|32bit
Sat May  9 19:19:07 2020: configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
Sat May  9 19:19:07 2020: ALSA: final selected sample format for capture: 32bit integer little-endian
Sat May  9 19:19:07 2020: ALSA: use 2 periods for capture
Sat May  9 19:19:07 2020: ALSA: final selected sample format for playback: 32bit integer little-endian
Sat May  9 19:19:07 2020: ALSA: use 2 periods for playback
Sat May  9 19:19:07 2020: port created: Midi-Through:midi/playback_1
Sat May  9 19:19:07 2020: port created: Midi-Through:midi/capture_1
Sat May  9 19:19:07 2020: port created: CH345:midi/playback_1
Sat May  9 19:19:07 2020: port created: CH345:midi/capture_1
Sat May  9 19:19:07 2020: ERROR: Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
Sat May  9 19:19:07 2020: ERROR: AcquireSelfRealTime error

```

What's weird is that Qjackctl starts jack somehow ignoring those errors and in the Status tab it tells me "Realtime Mode: Yes".

What do I miss?

Thanks.

---

### Post by 0x656b694d on 2020-05-09
Hm, with a lowlatency kernel everything works fine.

I thought we could use now the generic kernel.

---


---
title: "Pulseaudio playback freezes with ESI juli@ soundcard"
date: 2009-11-07
forum: Multimedia Software
---

### Post by barisurum on 2009-11-07
After a while the playback freezes and continues when I restart playing a file (mp3, ogg, wav etc.). Pulseaudio messages in messages log:

Quote:
Sep 20 17:56:33 barubuntu pulseaudio[2486]: lock-autospawn.c: Cannot access autospawn lock.
Sep 20 18:01:33 barubuntu kernel: [ 79.000145] Clocksource tsc unstable (delta = -81507666 ns)
Sep 20 18:21:40 barubuntu pulseaudio[3029]: ratelimit.c: 7 events suppressed
Sep 20 18:29:50 barubuntu pulseaudio[3080]: ratelimit.c: 7 events suppressed
Sep 20 20:32:13 barubuntu pulseaudio[3624]: ratelimit.c: 7 events suppressed
Sep 20 21:10:07 barubuntu pulseaudio[3933]: pid.c: Stale PID file, overwriting.
Sep 20 21:11:04 barubuntu pulseaudio[3933]: ratelimit.c: 7 events suppressed

Does anyone have the same problem? My soundcard is an ESI Julia envy24 HTS

---

### Post by barisurum on 2009-11-21
Forget about it. I got rid of pulseaudio and installed esound daemon and sound works now.

---


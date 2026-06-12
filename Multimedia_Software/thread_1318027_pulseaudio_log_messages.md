---
title: "pulseaudio log messages"
date: 2009-11-07
forum: Multimedia Software
---

### Post by chronos87lm on 2009-11-07
After I installed Ubuntu 9.10 I noticed a many log messages from pulseaudio in "user.log" section from System Log Viewer:

Nov 7 12:20:07 ubuntu pulseaudio[1440]: ratelimit.c: 16 events suppressed
Nov 7 12:20:12 ubuntu pulseaudio[1440]: ratelimit.c: 13 events suppressed
Nov 7 12:20:21 ubuntu pulseaudio[1440]: ratelimit.c: 8 events suppressed
Nov 7 13:26:53 ubuntu pulseaudio[1441]: ratelimit.c: 109 events suppressed
Nov 7 13:27:15 ubuntu pulseaudio[1441]: ratelimit.c: 90 events suppressed
Nov 7 13:27:44 ubuntu pulseaudio[1441]: ratelimit.c: 94 events suppressed
Nov 7 13:36:00 ubuntu pulseaudio[1441]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 7 13:36:00 ubuntu pulseaudio[1441]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_via82xx'. Please report this issue to the ALSA developers.
Nov 7 13:36:00 ubuntu pulseaudio[1441]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 7 13:54:14 ubuntu pulseaudio[1441]: ratelimit.c: 88 events suppressed
Nov 7 13:56:21 ubuntu pulseaudio[1441]: ratelimit.c: 89 events suppressed
Nov 7 14:14:44 ubuntu pulseaudio[1441]: ratelimit.c: 72 events suppressed
Nov 7 14:16:20 ubuntu pulseaudio[1441]: ratelimit.c: 91 events suppressed
Nov 7 14:17:41 ubuntu pulseaudio[1441]: ratelimit.c: 82 events suppressed
Nov 7 14:20:51 ubuntu pulseaudio[1441]: ratelimit.c: 91 events suppressed

This is just part of the log. There are a lot of similar messages.
Is this bad? Should I worry?

---

### Post by Belizeian on 2010-01-03
I also have this issue, sound works fine it's just cluttering up the log file with that message

---

### Post by me13221 on 2010-03-31
I have this problem too.  Has anyone filed a bug?

---

### Post by me13221 on 2010-04-01
Bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/444675](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/444675)

It's certainly of minor importance.

---


---
title: "Pulseaudio errors - Stale PID and Operation not permitted"
date: 2009-03-15
forum: Multimedia Software
---

### Post by davidpbrown on 2009-03-15
At each boot /var/log/messages gets errors from pulseaudio..

> pulseaudio[17304]: ltdl-bind-now.c: Failed to find original dlopen loader.
pulseaudio[17306]: pid.c: Stale PID file, overwriting.
pulseaudio[17306]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
pulseaudio[17306]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

There was [a thread]("http://ubuntuforums.org/showthread.php?p=5956390") about this, before Intrepid came out, that is now closed.
Adding user to pulse* groups doesn't seem to have had any effect.

Is there a simple fix for this?..

---


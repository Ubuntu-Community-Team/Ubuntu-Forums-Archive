---
title: "weird pulseaudio problems, can be rtkit-daemon related"
date: 2011-11-02
forum: Multimedia Software
---

### Post by vangop on 2011-11-02
Hi,
I have the following symptoms:
while talking over the skype after ~30min of conversation I can no longer hear the other party. They cannot hear me as well. 
The system no longer plays any sounds.
Upon killing skype everything is fine.
The syslog has:
```
Nov  2 18:29:15 illidan rtkit-daemon[2133]: Successfully made thread 3525 of process 3525 (n/a) owned by '1000' high priority at nice level -11.
Nov  2 18:29:15 illidan rtkit-daemon[2133]: Supervising 1 threads of 1 processes of 1 users.
Nov  2 20:29:15 illidan pulseaudio[3525]: [pulseaudio] pid.c: Stale PID file, overwriting.
Nov  2 18:29:16 illidan rtkit-daemon[2133]: Successfully made thread 3534 of process 3525 (n/a) owned by '1000' RT at priority 5.
Nov  2 18:29:16 illidan rtkit-daemon[2133]: Supervising 2 threads of 1 processes of 1 users.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Successfully made thread 3535 of process 3525 (n/a) owned by '1000' RT at priority 5.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Supervising 3 threads of 1 processes of 1 users.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Successfully made thread 3536 of process 3525 (n/a) owned by '1000' RT at priority 5.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Supervising 4 threads of 1 processes of 1 users.
Nov  2 20:29:17 illidan pulseaudio[3525]: [pulseaudio] bluetooth-util.c: Error from RegisterEndpoint reply: org.freedesktop.DBus.Error.UnknownMethod
Nov  2 20:29:17  pulseaudio[3525]: last message repeated 2 times
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Successfully made thread 3538 of process 3538 (n/a) owned by '1000' high priority at nice level -11.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Supervising 5 threads of 2 processes of 1 users.
Nov  2 20:29:17 illidan pulseaudio[3538]: [pulseaudio] pid.c: Daemon already running.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Successfully made thread 3540 of process 3540 (n/a) owned by '1000' high priority at nice level -11.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Supervising 5 threads of 2 processes of 1 users.
Nov  2 20:29:17 illidan pulseaudio[3540]: [pulseaudio] pid.c: Daemon already running.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Successfully made thread 3542 of process 3542 (n/a) owned by '1000' high priority at nice level -11.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Supervising 5 threads of 2 processes of 1 users.
Nov  2 20:29:17 illidan pulseaudio[3542]: [pulseaudio] pid.c: Daemon already running.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Successfully made thread 3544 of process 3544 (n/a) owned by '1000' high priority at nice level -11.
Nov  2 18:29:17 illidan rtkit-daemon[2133]: Supervising 5 threads of 2 processes of 1 users.
Nov  2 20:29:17 illidan pulseaudio[3544]: [pulseaudio] pid.c: Daemon already running.

```
First of all wtf is wrong with the time? Why rtkit-daemon lives 2 hours back in past?? 
Can it be caused by this rtkit? Thanks!

---


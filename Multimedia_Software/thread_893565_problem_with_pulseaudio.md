---
title: "problem with pulseaudio"
date: 2008-08-18
forum: Multimedia Software
---

### Post by existPierre on 2008-08-18
Hi,

i have a problem with pulse. After command pulseaudio -vv this log

```
peter@linux-pc:~$ pulseaudio -vv
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
E: main.c: Unknown command: ; daemonize = no
E: main.c: Failed to initialize daemon.
I: main.c: Daemon terminated.

```

I have a mistake in dameon.conf , restart and pulseaudio not working. When i replaced backup deamon.conf, same problem. 

Pulseaudio not working and alsa too :(

```

peter@linux-pc:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

```

Can u help me with this problem? thx

---

### Post by existPierre on 2008-08-26
nothing :( pls help

---


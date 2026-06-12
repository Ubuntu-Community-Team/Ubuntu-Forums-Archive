---
title: "Pulseaudio Latency"
date: 2009-06-17
forum: Multimedia Software
---

### Post by eloydark on 2009-06-17
I am having a sound problem which I believe is pulseaudio related. I have edited daemon.conf is such a way to enable 6 channel output and subwoofer output. The file is now this:

```
; daemonize = no
; fail = yes
; disallow-module-loading = no
; disallow-exit = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = ffmpeg
; disable-remixing = no
disable-lfe-remixing = no

; flat-volumes = yes

; no-cpu-limit = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rtttime = 1000000

; default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10
```

And I have noticed that every now and then, pulseaudio skips the output for a moment, like a lag, and then continues from the place it should be (skipping like half a second of music). This is extremely annoying, especially since I listen to music very often and it skips 2 or 3 times in every song. This I believe shows that the latency is too high. My hardware is well above average power and does not justify this kind of lag. Quad Core Phenom 9950 with 8GBs of RAM. What could be the problem and how can I fix this?

Thx in advance

---


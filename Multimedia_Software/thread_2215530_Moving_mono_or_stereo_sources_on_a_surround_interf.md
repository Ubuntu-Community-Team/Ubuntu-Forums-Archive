---
title: "Moving mono or stereo sources on a surround interface in Pulseaudio"
date: 2014-04-07
forum: Multimedia Software
---

### Post by Ranko Kohime on 2014-04-07
Is it possible to reassign the channel that a source gets played on in the sink?  So that, for example, I can place a mono sound in any arbitrary channel of the sink, or a stereo source in any 2 channels, (not necessarily matching channels, say LF and RR)...

Is this kind of fine-tuning supported by Pulse?

---

### Post by tgalati4 on 2014-04-07
No, it is not possible.  (That should get some responses.)

There may be a way to remap the channels.  But I don't know it.

tgalati4@Mint14-Extensa /etc/pulse $ pulseaudio --dump-conf
### Read from configuration file: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
local-server-type = user
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-2.1/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
alternate-sample-rate = 48000
default-sample-channels = 2
**default-channel-map = front-left,front-right**
default-fragments = 8
default-fragment-size-msec = 10
enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
deferred-volume-extra-delay-usec = 0
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 1000000

---


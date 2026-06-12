---
title: "C'mon we can stomp bug #445849"
date: 2010-04-18
forum: Multimedia Software
---

### Post by Jive Turkey on 2010-04-18
In reference to [Highpitched Rattling like Sound with 5.1 Surround Configuration on Karmic Koala]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849") which as yet still persists in lucid beta 2.

I think I may have made some progress toward a working config that significantly reduces this issue in Lucid beta 2 (installed w/ alternate amd64 CD).  I have the Intel HDAudio (ICH10) onboard audio chip (:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller) and the following steps seem to have resulted in pretty decent 5.1 analog output in 10.04 amd64.  I wouldn't say that its perfect but the artifacts I'm hearing may be from the media I'm testing with.  You may be able to duplicate my results with the following steps:

1. Set profile to Analog Surround 5.1 Output + Analog Stereo Input (I haven't tested any audio input whatsoever) in Sound Preferences > Hardware tab

2. Adjust /etc/pulse/daemon.conf to appropriately reflect these values:
```
:~$ pulseaudio --dump-conf
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
cpu-limit = no
enable-shm = yes
flat-volumes = no
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-0.9.21/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = auto
log-level = notice
resample-method = speex-float-9
enable-remixing = yes
enable-lfe-remixing = yes
default-sample-format = s24le
default-sample-rate = 48000
default-sample-channels = 6
# This channel map seems to have been automatically applied after rebooting, my actual conf reads: "default-channel-map = front-left,front-right,rear-left,rear-right,center,LFE
default-channel-map = front-left,front-left-of-center,front-center,front-right,front-right-of-center,rear-center
default-fragments = 8
default-fragment-size-msec = 10
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
```

3. make sure relavent volume controls in alsamixer are set to 100%

4. Reboot or otherwise bounce pulseaudio to apply the config.

Note: A lot of the problems discussed in bug #445849 still persist, namely:
1. Some crackling when moving volume sliders.
2. Balance, Fade, Subwoofer volume sliders in Sound preferences remain absolutely useless.
3. /var/log/messages gets entries like this:
```
Apr 18 14:48:24 plug1 pulseaudio[2426]: ratelimit.c: 1493 events suppressed
Apr 18 14:48:29 plug1 pulseaudio[2426]: ratelimit.c: 1708 events suppressed
Apr 18 14:48:34 plug1 pulseaudio[2426]: ratelimit.c: 1829 events suppressed
Apr 18 14:48:39 plug1 pulseaudio[2426]: ratelimit.c: 1923 events suppressed
Apr 18 14:48:44 plug1 pulseaudio[2426]: ratelimit.c: 1844 events suppressed
Apr 18 14:48:49 plug1 pulseaudio[2426]: ratelimit.c: 1926 events suppressed
```

I'm hoping to encourage discussion of this because I feel this crucial to HTPC use case of ubuntu.  Any insight is greatly appreciated.

---

### Post by Jive Turkey on 2010-04-18
After some more testing I've found that PA recreates ~/.pulse with settings that break audio playback for me.  I created an alias in my bashrc file as a workaround until I can figure the problem out.  This restores audio functionality for me after I run "ih8pa" in a terminal.
```
alias ih8pa='rm -rf ~/.pulse && sudo /etc/init.d/pulseaudio restart';

```

---


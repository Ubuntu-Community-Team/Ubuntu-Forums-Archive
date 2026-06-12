---
title: "hp2133 pulseaudio stuttering and high cpu"
date: 2011-05-24
forum: Multimedia Software
---

### Post by tlindvall on 2011-05-24
I have tested maverick and linux mint 10 in hp2133.  Looks like there is a problem with pulseaudio.  When using a recording application (gnome-sound-recorder or skype) and internal mic, pulseaudio eats all available cpu (cpu running 100%) and the sound is stuttering.  Arecord and aplay works fine without any problems so the problem seems to be related to pulseaudio.  I can get a little bit help when using tsched=0 setting, there is less stuttering, but pulseaudio still uses about 26% of cpu, which is way too much for this low end cpu.

I'm running out of ideas. Anyone having any suggestions?

---

### Post by scubascooby on 2012-02-19
Over 2 years on and I am still having this problem. Pulseaudio has rendered this machine almost useless.

I gave up on Skype and tried Ekiga/Empathy but Pulseaudio ruins that too. I tried all sort of alsa fixes here are dozens of "solutions" on the net but none work fully.

How do I stop it from grabbing so much cpu ?

```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1700 j        9 -11  166m 8768 7208 S     32.5    0.9   0:11.59 pulseaudio         
 1663 j        20   0  442m  97m  29m S    29.1   10.5   1:18.47 firefox            
 1777 j        20   0  240m  52m  20m S    20.5    5.6   0:15.66 skype              

``````

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
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

#resample-method = speex-float-1
resample-method = trivial
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

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
; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10


```

---

### Post by scubascooby on 2012-03-19
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207135](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207135)

Why is this listed as fixed even though it clearly isn't ?

---


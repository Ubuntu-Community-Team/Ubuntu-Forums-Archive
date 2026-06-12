---
title: "Surround 5.1 rolls back to 2 channels"
date: 2011-10-18
forum: Multimedia Software
---

### Post by razor7 on 2011-10-18
Hi, after installing Ubuntu 11.10, i configured my Sound Settings to be 5.1 + analog input. It works ok, but after closing and reopening banshee, the sound channels rolls back to 2 channels, this also happens on changing the song playes (ie: next, previous) and also after a reboot.

In the configuration dialog, is still selected "5.1 + analog input" but no 5.1 sound at all, only default stereo 2 channels only.

To fix it i have to open sound settings and in the output tab reselect "Internal Analog surround 5.1"

My audio codec is Realtek ALC889

Is this fixable?

Thanks  alot!

---

### Post by razor7 on 2011-10-24
Hi, no clue on this...any ideas?

Thanks a lot in advise!

---

### Post by razor7 on 2011-11-10
Epic Bump!

---

### Post by razor7 on 2011-11-25
I'm the only facing this issue?

---

### Post by razor7 on 2011-12-01
The most bumped thread in history!

---

### Post by cbowman57 on 2011-12-01
Maybe this.

** Surround sound systems**

 Many people have a surround card, but have speakers for just two  channels, so PulseAudio cannot really default to a surround setup. To  enable all the channels, edit [COLOR=#222][FONT=monospace]/etc/pulse/daemon.conf[/FONT][/COLOR]: uncomment the default-sample-channels line (i.e. remove the semicolon  from the beginning of the line) and set the value to **6** if you have a *5.1* setup, or **8** if you have *7.1* setup etc.

*[copied from the ArchWiki]("https://wiki.archlinux.org/index.php/PulseAudio")

---

### Post by razor7 on 2011-12-01
Hi, thanks for the reply. 

That's exactly what I did before posting.

Attaching my daemon.conf file.

```

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
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
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
; default-script-file = /etc/pulse/default.pa

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
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
default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
; deferred-volume-safety-margin-usec = 8000
; deferred-volume-extra-delay-usec = 0

```

Thanks in advise!

---

### Post by cbowman57 on 2011-12-01
I haven't read anything on it but looking at that file I wonder if that default-channel-map also needs some hacking, but this is not my field of expertise.

---

### Post by razor7 on 2011-12-01
hi, no luck, changed 

default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

but no luck, same behaiviour, need to reselect 5.1 from "Output" tab

---

### Post by razor7 on 2011-12-06
Well, at least an answer in ask ubuntu

[http://askubuntu.com/questions/68865/sound-reverts-to-2-channels-from-5-1-analog/85702](http://askubuntu.com/questions/68865/sound-reverts-to-2-channels-from-5-1-analog/85702)

Works ok

---


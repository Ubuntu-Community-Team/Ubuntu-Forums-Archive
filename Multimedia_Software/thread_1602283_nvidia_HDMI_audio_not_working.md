---
title: "nvidia HDMI audio not working"
date: 2010-10-21
forum: Multimedia Software
---

### Post by Mikkel_ on 2010-10-21
Hi im trying to get my xbmc box running on an asus ion mobo. in gnome i set all audio output to the hdmi driver but im not getting any sound on the tv. Im a newbie by the way so it's problably some silly thing.. 
but i've included a link to my alsa information and pulseaudio settings in case it's a big thing.

[http://www.alsa-project.org/db/?f=e52c8d832a6ed029801b8e6fa3f2eb038a5057a8](http://www.alsa-project.org/db/?f=e52c8d832a6ed029801b8e6fa3f2eb038a5057a8)

and here's my pulseaudio conf dump:

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
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
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

---

### Post by Mikkel_ on 2010-10-22
anyone out there with an idea?

---

### Post by dartmusic on 2010-10-22
Never mind...

---

### Post by lidex on 2010-10-22
> **Mikkel_ said:**
> Hi im trying to get my xbmc box running on an asus ion mobo. in gnome i set all audio output to the hdmi driver but im not getting any sound on the tv. Im a newbie by the way so it's problably some silly thing.. 
but i've included a link to my alsa information and pulseaudio settings in case it's a big thing.

[http://www.alsa-project.org/db/?f=e52c8d832a6ed029801b8e6fa3f2eb038a5057a8](http://www.alsa-project.org/db/?f=e52c8d832a6ed029801b8e6fa3f2eb038a5057a8)

and here's my pulseaudio conf dump:

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
resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no
default-sample-format = s16le
default-sample-rate = 44100
default-sample-channels = 2
default-channel-map = front-left,front-right
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

Your alsa-info looks fine, I guess the next question is what video driver are you using? Have a look here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
[http://ubuntuforums.org/showthread.php?t=1542401](http://ubuntuforums.org/showthread.php?t=1542401)

---

### Post by Mikkel_ on 2010-10-23
thanks for that very helpful piece of forum post there lidex... i got my hdmi sound up and running :P

---


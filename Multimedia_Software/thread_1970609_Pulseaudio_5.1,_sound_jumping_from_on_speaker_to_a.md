---
title: "Pulseaudio 5.1, sound jumping from on speaker to another"
date: 2012-05-01
forum: Multimedia Software
---

### Post by jabgrall on 2012-05-01
Hello,

I am creating this new thread because I can't find a proper solution in any other thread.

I have a 5.1 sound system with a 7.1 sound card. The sound is going out well on stereo. But I got a really weird effect when I am configuring the 5.1 configuration of pulseaudio. When I am asking to send a sound to a specific speaker (for example, with "speaker-test -c 6 -t wav") the sound is jumping from one speaker to another on the same side. For example, if a request is done to one of the speaker of the "left" group (front-left, rear-left and centre), the sound is jumping from one speaker of the "left" group to another. The same goes for the "right" group (front-right, rear-right and sub-woofer).

I also tried with different configurations. With 2.0 and 4.0, everything is OK. But, with 4.1, 5.0 and 5.1, the sound is jumping from one speaker to another. And finally, with 7.1, the sound is sent to all the speakers of the same group (left or right), slowed down with a high pitch noise added to it.

I am now with Ubuntu 12.04. But, the problem was already existing with 11.10. At that time, I decided to pass to Alsa only. And everything was working properly. But, now, I don't really want to go back to Alsa only. Mainly because it is a quite long job to do the modification back to it. Because it is also hard to find software which are able to jump from one configuration of alsa with 2.0 up-mixed to another in 5.1 depending on the sound source read (xine makes the trick really well by the way). And finally because it doesn't solve the main problem to begin with.

From my test, I got to the conclusion that it was Pulseaudio which is the source of the problem. And more probably, that it is coming from a conflict in the distribution of the sound to the correct channels. It is happening each time I choose the physical line for the sub-woofer and the centre speaker. And probably increasing when the physical line for the side speakers are chosen.

So, I am open to any help that can solve the problem. As well as tips to where I should be posting this problem so it can be fixed.

For information, you can find the result of the following code: "wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh", on:

[HTML]http://www.alsa-project.org/db/?f=c18c94b6ee3bcbb9d90d502322c1ed6bb9f73530[/HTML]The sound card with the problem is: "NFORCE - Intel ICH with ALC850 at irq 23". The problem was already there before I added the "SAA7134" card.

Here is also the file "/etc/pulse/daemon.conf":

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

resample-method = speex-float-3
enable-remixing = yes
enable-lfe-remixing = yes

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
default-sample-rate = 48000
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe

default-fragments = 8
default-fragment-size-msec = 10

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0
```
Thank in advance.

---

### Post by jabgrall on 2012-05-01
I just realised that for the 4.0 configuration, the problem was still present but at a really lower level (really tiny glitches between two speakers of the same side). So, each time a physical line is added, the problem got worst.

---


---
title: "Garbled 5.1 sound since upgraded to 9.10 Karmic"
date: 2009-11-02
forum: Multimedia Software
---

### Post by jemdos on 2009-11-02
Greetings from Sunny Spain

Sound 5.1 was ok till I upgraded to Karmic. I do not understand what's wrong with the new version of the distro, but it's just plain weird.

So: I can listen to video files without going nuts if I "downgrade" to stereo. But when I try to use 5.1 sound, all channels output rubbish, that recalls me about what happens when you play multimedia files on very old computers... something like hiccups. 

As for audio files, there're high pitches and low noises (it looks like playing and old vinyl on and old turntable).

aplay -L
=========
shm_open() failed: Read-only file system
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

lspci -v
========
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: Giga-byte Technology Device ae01
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at bc00 [size=256]
	I/O ports at c000 [size=256]
	Memory at f0105000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0       <-------??

/etc/pulse/daemon.conf
======================
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
allow-module-loading = yes
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

resample-method = speex-float-1
enable-remixing = yes
enable-lfe-remixing = no

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

default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

---


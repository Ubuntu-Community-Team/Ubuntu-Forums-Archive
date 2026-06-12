---
title: "When using pulseaudio across network audio becomes very choppy, even on local machine"
date: 2009-01-27
forum: Multimedia Software
---

### Post by jerome1232 on 2009-01-27
I was messing with pulseaudio today to get the network features and I've got it working (I have a RTP multicast device, I can see it on the other computer) If I move a stream over to it, I can get it on the the other computer and I can get it on the local machine as well but the sound is VERY choppy.

According to the pulse audio the fix is to downsample the audio. I guessed that editing /etc/pulse/daemon.conf is the way to do this.

I think I have it downsampled to 4000 hz with no improvment yet. I was issuing "sudo service pulseaudio restart" commands between changes, I wasn't sure if that was actually restarting the pulse audio daemon or not so I restarted as well for good meseaure on the last change (to 4000 hz)

Here's my daemon.conf is there something I'm missing or something else to change the sampling rate?

```
# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
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
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
; default-sample-rate = 4000
; default-sample-channels = 2

default-fragments = 8
default-fragment-size-msec = 10

```

---

### Post by jerome1232 on 2009-01-28
Bump

---

### Post by markbuntu on 2009-01-28
You can try changing the default fragments and default fragment size. This sometimes helps with choppy audio.


default-fragments = 5
default-fragment-size-msec = 25

This will send fewer but larger chunks across your network. Sending high quality sound across a network can use a lot of bandwidth and sound will get choppy on a busy or slow network.

There is more info here.

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

---

### Post by jerome1232 on 2009-01-28
That certainly helped, although still a bit (well I can tell that's it music now) choppy. That wiki was where I got the idea to lower sampling rate.

But it seems like it shouldn't be this bad, on my computer If I go into Volume Control and right click the audio stream and move it to the RTP Multicast device it becomes choppy even on the local computer.

I know my network is 100 megabits per second which comes out to well over the 1.33 megabytes per second stated in the wiki.

Would that be a result of network slowness (isn't that just going over the loopback interface?)

---

### Post by markbuntu on 2009-01-29
You could snoop the network and ping around to see what's going on. A firewall or virus checker will cetainly slow things up but you shouldn't have that problem with an internal network.

---

### Post by ErwinJunge on 2009-05-14
Maybe you figured this out by yourself by now, but you didn't read/understand the instructions in that file properly.

> ## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.


The line you have been editing clearly has a ; in front of it. This means it is a comment and not actually read by the program. 

What you should have done is copied the line, pasted it at the bottom (optionally add a comment of your own explaining what you are trying to do), removed the ";" and then edited the number. Restart the service afterwards ofcourse.

The reason for those commented lines is so that you can easily see the defaults the program uses. They are only there for reference and you shouldn't edit those lines.

Hope this helps.

---


---
title: "MIC setup with PulseAudio"
date: 2008-06-05
forum: Multimedia Software
---

### Post by MemoryDump on 2008-06-05
hi all,

I managed to get my 2 sound cards configured for Pulse usage! w00t

So now I have my 4.1 speakers working properly with my Audigy2 card! 

My prob now is that I'm trying to get my second sound card (the on-board one) to work strictly for my headset.
When I go to the sound options I can only get it to work if I select OSS. Shouldn't Pulse manage it now? I've tried setting it to pulse, however it doesn't work no matter what option I select in the drop down. (see attachments)

here are my config files:

**[COLOR="Red"]/etc/asound.conf[/COLOR]**
```
pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

pcm.headset {
        type hw
        card 0
}

ctl.headset {
        type hw
        card 0
}

```

**[COLOR="Red"]/etc/pulse/default.pa[/COLOR]**
```
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
load-module module-alsa-sink device=surround41:Audigy2 sink_name=Audigy2 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe
load-module module-alsa-source device=hw:Audigy2
load-module module-alsa-sink device=front:ICH5 sink_name=ICH5
load-module module-alsa-source device=hw:ICH5

### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif
#load-module module-alsa-sink device_id=0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-source input

```

**[COLOR="Red"]/etc/pulse/daemon.conf[/COLOR]**
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

; resample-method = speex-float-3
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
; default-sample-rate = 44100
 default-sample-channels = 4

; default-fragments = 4
; default-fragment-size-msec = 25

```

any help would greatly be appreciated ! :)

-MD

---

### Post by MemoryDump on 2008-06-06
still looking for some help! only thing giving me a headache on Hardy.

---

### Post by MemoryDump on 2008-06-07
really hoping to find some help here! I've tried #pulseaudio on IRC and there's normally nobody there answering questions :(

---

### Post by marseille on 2008-07-11
yah, me too...

got no mic sound in pulseaudio.  plz help.  much obliged.

:guitar:

---


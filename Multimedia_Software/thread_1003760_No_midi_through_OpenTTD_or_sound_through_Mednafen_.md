---
title: "No midi through OpenTTD or sound through Mednafen (using a52 plugin)"
date: 2008-12-06
forum: Multimedia Software
---

### Post by tghe-retford on 2008-12-06
I have setup my sound system as per the thread linked below on how to allow Pulseaudio to output surround sound using ALSA's a52 plugin for my surround sound system.

[http://ubuntuforums.org/showthread.php?t=714712](http://ubuntuforums.org/showthread.php?t=714712)

Now on the whole it works great and sounds much better than the default Ubuntu setup - even AC3 passthrough works as expected through mplayer with a tweak, however - OpenTTD now no longer outputs any music, only sound effects and Mednafen will not output sound without immense slowdown.

With OpenTTD, midi sound will not work. Timidity++ can play midi files through the GTK+ interface if I do the following:

```
timidity -iA -Os -ig
```

And it can also play midi files through the command line using -iA -Os, but I can't figure out anyway to get OpenTTD to play ball.

As well, Mednafen won't play any sound, no matter what output I use. If I use *padsp* then sound does work, however then the frame rate is so slow the game I want to play is unplayable and the sound is broken up.

Any suggestions as to how I can get sound to work considering the tweak I have made to enable a52 output? I'd rather keep the improved sound that the ALSA a52 plugin gives through Pulseaudio, but it would be nice to get sound working again in the above applications.

My /etc/asound.conf as edited per thread linked above:

```
pcm.a52encode {
	type a52
}

pcm.!default {
	type pulse
}

ctl.!default {
	type pulse
}

pcm.pulseaudio a52encode

ctl.pulseaudio {
	type hw
	card 0
}
```

And /etc/pulse/default.pa, as edited per thread linked above:
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
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

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

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

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

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input

### Surround sound guff
load-module module-alsa-sink device=pulseaudio rate=48000 channels=6 sink_name=alsa_surround mmap=0
set-default-sink alsa_surround
```
Thanks in advance.

---


---
title: "How does module-pipe-sink in PulseAudio work???"
date: 2009-06-26
forum: Multimedia Software
---

### Post by alvaroalo on 2009-06-26
[SIZE=3]Hey!!!!

I have a big problem.

I want to pipe the output from an application to a fifo, so that I could later on use this fifo as an input to ffmpeg. I have started the PulseAudio qith the default configuration, this is[/SIZE]

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

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif


### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink file=/tmp/sound

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp auth-anonymous=1
#load-module module-native-protocol-tcp auth-anonymous=1
#load-module module-zeroconf-publish
#load-module module-pipe-sink file=/tmp/sound

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load the null-sink it will be used for storing the audio stream in order # to be inserted with ffmpeg
#load-module module-null-sink sink_name=sink1

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif


### Make some devices default
#set-default-sink output
#set-default-source input


[SIZE=3]Then, I tried to create a pipe_sink

[SIZE=1]pactl load-module module-pipe-sink file=/alvaro/soundido
PULSE_SINK=fifo_output

[SIZE=3]However, after playing Rhythmbox, I discovered that the file /alvaro/soundido was completely empty, in other terms, nothing was transferred to it. I checked then the PulseAudio Device Chooser, and I discovered that the songs played are running under the sink named alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0, instead of the fifo_output I have established[/SIZE]
[/SIZE]
Any idea??? Thanks!!!!
[/SIZE]

---


---
title: "RME HDSP through PulseAudio on Ubuntu"
date: 2011-10-29
forum: Multimedia Software
---

### Post by hacor on 2011-10-29
Best Ubuntu users,

For some time now I've been experimenting on using my RME HDSP audio card on Ubuntu. Most dedicated software recognizes the card but I wanted to use my HDSP card as well for system sounds (through PulseAudio) for watching movies through my good speakers, etc.

After looking around on the web for hours, I found some snippets of info everywhere and I want to put them all together in here:

change the contents of** /etc/pulse/default.pa** into:

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

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### manually load driver for HDSP Digiface

load-module module-alsa-sink device=hw:DSP sink_name=HDSP_PLAYBACK rate=48000 format=s32le tsched=0 channels=18 channel_map=aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,front-left,front-right,side-left,side-right,side-left,side-right,rear-left,rear-right,aux0,aux1

load-module module-alsa-source device=hw:DSP source_name=HDSP_CAPTURE rate=48000 format=s32le tsched=0 channels=18 channel_map=aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,front-left,front-right,side-left,side-right,side-left,side-right,rear-left,rear-right,aux0,aux1

### Automatically load driver modules depending on the hardware available
### .ifexists module-udev-detect.so
### load-module module-udev-detect
### .else

### Alternatively use the static hardware detection module (for systems that
### lack udev support)
### load-module module-detect
### .endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
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

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Honour intended role device property
load-module module-intended-roles

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
load-module module-cork-music-on-phone

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

### Point pulseaudio to the Multiface
set-default-sink HDSP_PLAYBACK
set-default-source HDSP_CAPTURE
```Through the Software Center (or Synaptics packet manager) Remove your ALSA-tools and ALSA-tools GUI if they are more recent then 1.0.23. And install the 1.0.23 version instead, you can download .deb files on the web. The newer ALSA-tools versions don't include HDSPmixer anymore for some reason. So watch your updates, don't overwrite the older version again with a more recent one!

Reboot and start 
```
hdspmixer
```from a terminal. You need to start hdspmixer every time you boot, otherwise you won't have sound!

Good luck

Hans

---


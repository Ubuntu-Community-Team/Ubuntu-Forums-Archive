---
title: "AlsaMixer Master Muted on Startup"
date: 2009-12-02
forum: Multimedia Software
---

### Post by chrisolof on 2009-12-02
This is strange, but out of the blue last week I booted into Ubuntu (9.10 Desktop 64-bit) and had no sound.  After searching a bit I was able to fix the problem by launching alsamixer from the terminal and unmuting the "Master" channel.  Nothing in "Sound Preferences" addresses this - only alsamixer.

The problem is that every time I boot into the system there's no sound until I launch alsamixer and unmute the master channel again.

Anyone have any ideas?

I have a feeling it was related to an update applied by updatemanager because other than that I haven't messed with anything.

Here's my setup:
description: Audio device
product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
vendor: nVidia Corporation
physical id: 7
bus info: pci@0000:00:07.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
resources: irq:21 memory:f9e78000-f9e7bfff

---

### Post by xc3RnbFO8P on 2009-12-02
Maybe this bug:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/352732")

---

### Post by chrisolof on 2010-01-10
Thanks Ringi - that was the bug and comment #77 fixes it:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/77]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/77")

---

### Post by ktechman on 2010-01-11
The above also worked for me.

> This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line

load-module module-device-restore

in /etc/pulse/default.pa with

#load-module module-device-restore

Perhaps you have to logout, kill all pulseaudio daemons, login, adjust volumes, logout and login again to see if it works.

On-board sound Via VT1708B 
Asus M3A78 Motherboard

Thank you Chrisolof for the information

Ktechman

---

### Post by PCman13 on 2010-02-23
Thanks! The sound is now enabled by default, but it still doesn't remember the exact volume: on startup it is 28%. :confused: 

The contents of /etc/pulse/default.pa are the folowing:

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
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Automatically restore the volume of streams and devices
#load-module module-device-restore
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

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

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
#load-module module-cork-music-on-phone

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
```Is there still something wrong?:confused:

---

### Post by keesp on 2012-07-04
Had the same problem with Xubuntu 12. removed Pulseaudio and everything seems to work ok

---


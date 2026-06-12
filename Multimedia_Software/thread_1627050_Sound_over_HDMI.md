---
title: "Sound over HDMI"
date: 2010-11-21
forum: Multimedia Software
---

### Post by ThinkXLinux on 2010-11-21
Hi all. I've been playing around with Ubuntu 10.04 for a while and I really love it. It's been my main OS for about 3 months now. Anyways, I'm attempting to get sound to work via my displayport on my thinkpad t410 using a displayport to HDMI adapter and an HDMI cable hooked to my TV.(I want to have sound play through my TV's speakers) So far the video works using the latest Nvidia drivers. I know that my laptop supports sound through the displayport as I've been able to get both sound and video using the same hardware setup but in Windows 7. I've done alot of digging around the forums and everywhere else that showed up on google. No luck so far. I'm not sure how to get the sound working... When running the "sudo aplay -l" command in terminal, I get
 **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
So obviously it recognizes the HDMI connection. Also, in sound preferences I have the option to select HDMI digital sound. When doing so however, there is no sound from anything (Rythmbox, Youtube, Songbird, Pandora, etc...) 
Any advice and/or suggestions are very greatly appreciated. If any additional information is needed I will be happy to provide it. Thank you in advance for your help.

---

### Post by efflandt on 2010-11-21
In **alsamixer** to go F6 **HDA NVidia** and unmute all the ports (with **m**) so they are all 00 instead of any MM.  Then try the following, substituting 1,7 1,8 1,9 until you see which one works:

```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
```In my case it was 1,9 so I added a line to /etc/pulse/default.pa

```
load-module module-alsa-sink device=hw:1,9
```The speaker test in Sound Preferences > Hardware may not work. But try Rythmbox and see which "Output" devices work (you may end up with a 3rd device that does not work).  In my case "HDA NVidia" worked for HDMI, but the one that said "(HDMI)" did not.

---

### Post by ThinkXLinux on 2010-11-21
Thank you very much for your quick reply.I am away from my main computer and will be so for a little while. (Finals are coming up and I'm doing a lot of studying) As soon as I am able, I will be testing your proposed method. Again, thank you

---

### Post by ThinkXLinux on 2010-11-23
I tried your solution and I get sound! For me it was device 1,7. I have a question about the 2nd part of your instructions though. To what part of /etc/pulse/default.pa should I add the line of code? I took a look and I'm not sure where to input it. Thank you so much

---

### Post by ThinkXLinux on 2010-11-23
I added the line and now my /etc/pulse/default.pa reads....

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
#load-module module-alsa-sink device=hw:1,7
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

The sound works but I'm getting this horrible high pitched static. Any ideas?

---

### Post by efflandt on 2010-11-24
Note that anything after # in a line is considered a comment.  So try uncommenting that line by removing the #:

```
### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
**load-module module-alsa-sink device=hw:1,7**
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink
```Then see if you get stereo HDMI sound when you select **HDA NVidia** in the Output tab of Sound Preferences.  I have not done multi-channel audio because my analog sound is a 2.1 speaker system and HDMI on my TV just has the 2 speakers.

---


---
title: "hdmi surround sound center channel not working in lucid with nvidia gt240 chipset"
date: 2010-11-02
forum: Multimedia Software
---

### Post by deoanam2002 on 2010-11-02
I got my NVidia Gt240 video card working with full HDMI surround sound, piped to a Sony receiver.
Then, suddenly (and days later), the center channel seemed to stop working (no dialogue audible on video, just the background noises).

If I run 
```
speaker-test -D hdmi:NVidia -c6 -twav
```
I only get front left and front right giving any sound.

Edit: The only thing I can think of that may have changed anything is that I installed indicator-sound through synaptic.

Edit: Specifically, I am using smplayer, and in the audio settings my output driver is alsa (1.3 - HDA NVidia). This bypasses the system's default sound output setting. If, in smplayer, I go to Audio->Channels and select "Stereo", I get a full stereo sound through HDMI without a problem. It's when I enable either 4.0 surround or 5.1 surround that I only get left and right channels with no center channel (making it so that I can't hear dialogue, only background noise and music). I'm using matroska files at 720p.

Any ideas? Thanks in advance.
I'm running Lucid LTS.

I have no .asoundrc

alsamixer for HDA NVidia gives me only one listed channel entry, "S/SPDIF" which has no volume control, but can be muted and unmuted. It is currently unmuted.

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

asound.conf
```

#
# Place your global alsa-lib configuration here...
#

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


```

cat alsa-base.conf
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
#options snd-hda-intel enable_msi=0
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


```

default.pa
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
matt@matt-ubuntu:/etc/pulse$ ls
client.conf  daemon.conf  daemon.conf.bak  default.pa  system.pa
matt@matt-ubuntu:/etc/pulse$ cat systemp.pa
cat: systemp.pa: No such file or directory
matt@matt-ubuntu:/etc/pulse$ cat /etc/pulse/daemon.conf
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
; allow-module-loading = yes
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
; enable-remixing = yes
; enable-lfe-remixing = no

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
; default-sample-rate = 44100
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

```

---

### Post by deoanam2002 on 2010-11-02
Problem is solved thanks to this post:
[http://ubuntuforums.org/showthread.php?t=755479](http://ubuntuforums.org/showthread.php?t=755479)

All I had to do was create the ~/.asoundrc file and put this in it:

```

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}

```

Edit: To be clear, this fixed the problem not only in smplayer, but also for 
```
speaker-test -D hdmi:NVidia -c6 -twav
```
which now works flawlessly, giving me a report through each channel as it is supposed to.

Woot! :guitar:

---

### Post by deoanam2002 on 2010-11-03
And then I rebooted, and it went back to the same problem! :confused:
And now it seems impossible to fix.
Is this weird that I should be getting perfect surround sound one minute, and then gone the next? Can anyone see why this might happen based upon what I've listed above?
Thanks

---

### Post by deoanam2002 on 2010-11-03
Found a temporary workaround:
With the .asoundrc setup mentioned above, I go into sound preferences:
- select hdmi as the output
- change the hardware setting for the onboard card to Analog 5.1 + analog stereo input.

Then in smplayer, select "pulse" as audio output.

This gives me surround sound on my 720p mkv files.

HOWEVER: under this configuration, speaker-test doesn't output any sound.
And if I want to use my onboard card, I have to change the output setting back to it in sound preferences, which is a bit of a pain.
When surround sound worked before as reported, I didn't need to do this workaround.

---


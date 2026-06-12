---
title: "ALC882 and Pulseaudio in Lucid"
date: 2010-08-09
forum: Multimedia Software
---

### Post by AP0ll0UK on 2010-08-09
Does anyone know if there is a guide to getting an ALC882 working with Pulseaudio under Lucid please?

I have tried the steps outlined in this post - [http://ubuntuforums.org/showthread.php?t=1046137&highlight=model%3D](http://ubuntuforums.org/showthread.php?t=1046137&highlight=model%3D) but unfortunately I am still only getting stereo sound and not the 5.1 channels that I should be getting.

Any suggestions welcome.

---

### Post by lidex on 2010-08-09
Pulse Audio defaults to 2 channels. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1491347](http://ubuntuforums.org/showthread.php?t=1491347)
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

---

### Post by AP0ll0UK on 2010-08-12
Thanks for the info.

I'm running through the steps now but without much success unfortunately. I'll post more details once I've had a bit more of play.

Out of curiousity, why is it such a chore to enable 5.1 within Lucid?

The thing that bugs me is that before I rebuilt my Lucid box a few weeks ago, the audio side of things was working fine.

---

### Post by AP0ll0UK on 2010-08-12
Ok, I'm not having much luck at all. I've posted some info below so it might give some of you a clue as to whats wrong:-


> 
**dave@hermes:~$ aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 1: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> 
**dave@hermes:~$ aplay -L**


null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output


> 
**dave@hermes:~$ sudo nano /home/dave/.asoundrc**

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
# replace the following with the proper path:
</home/dave/.asoundrc.asoundconf>

pcm.pulseaudio {
	type pulse
}

ctl.pulseaudio {
	type pulse
}

pcm.pulseaudioplug {
	type plug
	slave.pcm "5to2"
}

pcm.!default {
	type upmix
	slave.pcm 5to2
	channels 6
}

ctl.!default {
	type pulse
}
# plughw must use your default sound card. Fix as needed.
# Card :# or card name may be added i.e. plughw:CMI8768
pcm.amp {
  type plug
  slave.pcm "plughw"
  slave.rate 44100
  slave.channels 2
  ttable {
	0.0=	3.101
	1.1=	3.101
  }
}

pcm.5to2 {
  type route
  slave {
    pcm amp
    channels 2
  }
  ttable {
	0.0=	 0.3225
	4.0=	 0.2280
	2.0=	-0.2633
	3.0=	-0.1862
	1.1=	 0.3225
	4.1=	 0.2280
	2.1=	 0.1862
	3.1=	 0.2633
  }
}


I have also tried :-

pcm.amp {
  type plug
**  slave.pcm "plughw:ALC882"**


> 
**dave@hermes:~$ sudo nano /home/dave/.asoundrc.asoundconf**
# defaults
#

# show all name hints also for definitions without hint {} section
defaults.namehint.showall off
# show just basic name hints
defaults.namehint.basic on
# show extended name hints
defaults.namehint.extended off
#
defaults.ctl.card 0
defaults.pcm.card 0
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format "unchanged"
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
# truncate files via file or tee PCM
defaults.pcm.file_format	"raw"
defaults.pcm.file_truncate	true
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0


> 
**dave@hermes:~$ sudo nano /etc/modprobe.d/alsa-base.conf**

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
options snd-hda-intel index=-2 model=ALC882
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


> 
**dave@hermes:/$ sudo nano ~/.pulse/daemon.conf**

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
; default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10


> 
**dave@hermes:/$ sudo nano /home/dave/.pulse/default.pa**

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


> 
**dave@hermes:/$ pkill pulseaudio; sleep 2; pulseaudio -vv**


I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.21-63-gd3efa-dirty
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimised build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 5d78ca454263eb55f4ec03014c41ce94.
I: main.c: Session ID is 5d78ca454263eb55f4ec03014c41ce94-1281637014.129783-1951157675.
I: main.c: Using runtime directory /home/dave/.pulse/5d78ca454263eb55f4ec03014c41ce94-runtime.
I: main.c: Using state directory /home/dave/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.


I've also tried installing PulseAudio Device Chooser, it runs in the taskbar for several seconds and then disappers.

Running Gnome Alsa Mixer just shows a blank grey form.

If anyone can please provide me with some guidance it would be greatly appreciated as this is driving me absolutely crazy.

---

### Post by lidex on 2010-08-13
OK, a couple of things. Probably need to get back to default settings first. Rename your asoundrc and asoundconf files. In alsa-base.conf you have a switch that really needs to go:
```
options snd-hda-intel index=-2 model=ALC882
```
Remove that pronto. Now reboot and post the output of these commands after:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
**Please also include the make/model of your PC/Laptop.**

---

### Post by AP0ll0UK on 2010-08-14
Ok, .asoundrc has been renamed as has .asoundrc.asoundconf.

Also, the line from alsa-base.conf has been removed and I rebooted.

Please find below the output you requested:-

> 
**dave@hermes:~$ uname -a**

Linux hermes 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux


> 
**dave@hermes:~$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> 
**dave@hermes:~$ dpkg -l | grep "alsa"**
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                          1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                     1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                                 1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                                14.3.0-1.1build1                                SoX alsa format I/O library
ii  linux-backports-modules-alsa-2.6.32-24-generic 2.6.32-24.17                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.24.25                                    Backported drivers for alsa-driver snapshot.


> 
**dave@hermes:~$ head -n 1 /proc/asound/card*/codec#***
Codec: Realtek ALC882


My PC is custom built, it's an Intel E6600, 3GB Ram, Nvidia 8400GS, all running off of an Abit AB9 Pro motherboard. There's some info about the board here - [http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AB9+Pro&fMTYPE=LGA775]("http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AB9+Pro&fMTYPE=LGA775")

As I mentioned previously, in my last build of Lucid [which I had to trash due to other issues] my audio was working fine and I didn't have to do anything to get 5.1 surround up and running, it just worked. With this build it only seems to want to output 2 channel stereo. Puzzling.

Many thanks for your help.

---

### Post by lidex on 2010-08-14
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by AP0ll0UK on 2010-08-14
Thanks for your reply.

Ok, I've added the line you suggest to alsa-base.conf and rebooted.

I've gone into alsamixer through the Terminal, selected the sound card, and the various channels are there for analog output, but my spdif is different from the rest, plus there are two of them which suggests that there are two spdif outputs but there is only one actually on the motherboard. One is S/PDIF, the other is S/PDIF Default PCM.

In the capture settings, I have set the S/PDIF in there two off, but having it either on or off has no affect on the sound coming out of the theatre kit.

Sorry for being a pain but do you have anymore suggestions please?

Screenshots attached.

---

### Post by lidex on 2010-08-15
Which ports are you using? Your profile is set to digital out, so you need to be using the spdif to your surround system. If you simply have speakers plugged into the analog jacks, it should be analog output. One thing I noted is the channel element in alsamixer. Your's is set to 6 channels. Toggle that to 8 channels using the up/down arrow keys. Now go back into sound preferences and toggle your profile setting.

---

### Post by AP0ll0UK on 2010-08-15
My PC is connected to my surrouned sound amp through spdif, Analog cables have never been in the equation.

I've checked that the rear speakers are working by changing the sound mode on the amp. The amp has mode which processes sound via whatever is fed to it, be that 2.1 or 5.1 and it shows on the amp what signal it believes it is being sent and it's not displaying 5.1.

When I try and play back a movie that has 5.1 audio, I've tried it in Totem and it just outputs stereo but there aren't many options within there to configure sound.

I've also tried VLC which is a bit more configurable, I've tried various combinations of using spdif, forcing detection of Golby Surround, and also flicking between ALSA output and Pulseaudio output, neither of which do anything other than stereo.

I've also done the obvious things like checking the connection between the PC and the amp but nothing has changed and I've not been round the back of it for a few months, the only thing that has changed is that I rebuilt my PC and reinstalled Ubuntu, it worked fine on the previous build without any setup or fine tuning, it just worked straight out of the box. That's why I'm so confused as my build of Ubuntu is exactly the same as the previous one. 

I ran a test on all the speakers and all of them output sound fine, the mode that forces 2.1 or stereo out of the front and rear speakers works fine, it's just trying to push 5.1 from the PC.

I've tried changing the channels from 6 to 8 in AlsaMixer as you suggested but unfortunately its still the same.

---

### Post by lidex on 2010-08-15
I have ALC883 (8 channel) on my desktop and changing from the default 6 to 8 channel gives me a few more profiles to choose from. What is happening in pavucontrol when you play audio? You're using a surround source, correct? I don't think stereo will output to 5.1

---

### Post by AP0ll0UK on 2010-08-15
I've tried various movie files, either xvid with ac3 or .x264 files which specifically have a 5.1 soundtrack, the same files I could play before the rebuild and would output 5.1 fine.

With regards to pavucontrol, the Output Devices tab shows 'Internal Audio Digital Stereo (IEC958)' with sliders for Front Left and Front Right, the Configuration tab is set to 'Digital Stereo (IEC958) Output + Analog Stereo Input'.

When I look at the list of Profiles, there are some 'Analog Surround' options, but the Digital profiles are all Stereo and not Digital Surround - Whether this is correct or not I don't know, does it show Digital Surround (IEC958) Output's on yours or are they listed as Digital Stereo?

---

### Post by AP0ll0UK on 2010-08-15
Sorry I'm lying, on the Playback tab of pavucontrol its showing all channels; front left, front right, rear left, rear right, front centre and subwoofer. 

But on the Ouput Devices tab, it's only showing front left and front right.

There is also a button called 'Lock Channels Together', I'm unsure whether this should be selected or unselected but neither seem to have any affect.

[Edit]
Attached are my list of profiles.
[/Edit]

---

### Post by lidex on 2010-08-15
You need a different input. You're using an analog stereo input.

---

### Post by AP0ll0UK on 2010-08-15
No sorry for confusing you, I'm not choosing the first profile or any of the Analog inputs, I'm selecting one of the following:-

Digital Stereo (IEC958) Ouput + Analog Stereo Input
Digital Stereo (IEC958) Ouput + Digital Stereo (IEC958) Input
Digital Stereo Duplex (IEC958)

---

### Post by AP0ll0UK on 2010-08-15
Please see attached.

---

### Post by lidex on 2010-08-15
> **AP0ll0UK said:**
>  the Configuration tab is set to 'Digital Stereo (IEC958) Output + Analog Stereo Input'.

That's what I was referring to. I see what you're saying though - I have the same. Hmm.

---

### Post by AP0ll0UK on 2010-08-15
Why does the input have an effect on what the output is? Truth be known I don't have any input going through my PC so it doesn't matter whether it is set to analog, digital or digital duplex as I don't need going into my PC, it's only the output I'm bothered about. 

I've tried all three different inputs previously and none seem to have any effect on what the output is.

---

### Post by AP0ll0UK on 2010-08-15
I'm curious, on your system, when your playing back a movie that uses all 6 or channels, in pavucontrol it shows you all channels. 

But in the Output Devices tab, does it just show you Front Left and Right in there, or does it show you all 6/8 channels?

If it shows them all then clearly there is something wrong with my system or config as it knows the movie I'm playing has 6 channels, but only choose to output 2 of them as per the Output Devices tab on my system where it only shows Front Left and Right.

---

### Post by lidex on 2010-08-15
You're right, I'm confusing myself. You did nothing on the previous install and had surround available at the spdif port?
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) (surround section)
[http://ubuntuforums.org/showthread.php?t=1452473](http://ubuntuforums.org/showthread.php?t=1452473)

---

### Post by AP0ll0UK on 2010-08-15
That's correct, on the previous install 5.1 audio just worked out of the box. That's one of things that frustrating me this time around in that it just refuses for some reason to work.

I have to hit the sheets now as I'm on GMT. I'll go through the guides you suggested but I have been through them once which resulted in the settings I had orginally before you told me to put them back to the defaults.

I'll give it a go tomorrow after work and report back. 

Many thanks again for your help, I know the issue isn't resolved but I do appreciate you trying to help me.

---

### Post by AP0ll0UK on 2010-08-16
I tried following some of those guides but Nothing seems to make any difference, I still end up with 6 channels in the playback tab but only two in the ouput tab - do you have all 6 or 8 of yours in the output tab?

I've also just rebuilt my system again from scratch this evening, ran with the defaults and still stereo, no surround. I'm gutted :(

---

### Post by AP0ll0UK on 2010-08-20
Unfortunately I'm still no further forward with this.

I don't know if I'm missing something obvious or what but despite rebuilding my system and trying some of the guides you pointed me towards I still can't get it working and surely if there were other Lucid 10.4 users out there with the same issues then they'd be screaming on the forums.

Please can you tell me exactly which bit of info I need to be looking at in order to get 5.1 setup with my spdif?

---

### Post by lidex on 2010-08-20
> **AP0ll0UK said:**
> Unfortunately I'm still no further forward with this.

I don't know if I'm missing something obvious or what but despite rebuilding my system and trying some of the guides you pointed me towards I still can't get it working and surely if there were other Lucid 10.4 users out there with the same issues then they'd be screaming on the forums.

Please can you tell me exactly which bit of info I need to be looking at in order to get 5.1 setup with my spdif?

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---


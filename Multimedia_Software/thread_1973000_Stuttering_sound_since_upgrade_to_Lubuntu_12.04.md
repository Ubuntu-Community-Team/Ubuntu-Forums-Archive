---
title: "Stuttering sound since upgrade to Lubuntu 12.04"
date: 2012-05-04
forum: Multimedia Software
---

### Post by Zogzog on 2012-05-04
Hello,

I've been using Lubuntu 11.10 on a Dell Latitude D520 and have experienced no special sound problems.

However, since upgrading to 12.04, after several minutes of using the computer the sound becomes stuttered. I'm mostly listening to YouTube and Pandora via Google Chrome though it affects also playing on Audacious.

Restarting the browser does not solve it, only restarting the computer.

Has anyone encountered a similar problem?
Are there any suggestions how this might be solved?

Thanks in advanced.

---

### Post by marinara on 2012-05-04
try the livecd, see if it stutters in that case

---

### Post by prshah on 2012-05-04
> **Zogzog said:**
> Restarting the browser does not solve it, only restarting the computer.


As a first step for troubleshooting, see if just restarting Pulseaudio fixes it, rather than restarting the entire computer.

To restart pulse, from a Terminal ("Dash Home"->"Terminal"), use the command ```
sudo service pulseaudio restart
#or, if no sudo access#
pulseaudio --kill && pulseaudio --start
```

If restarting pulseaudio fixes the sound, please post your pulse config files from /etc/pulse/ for further troubleshooting.

---

### Post by Jive Turkey on 2012-05-04
You're lucky it ever worked.  The audio has been defective for me since they implemented pulseaudio 3 years ago or so.

---

### Post by Zogzog on 2012-05-05
Thank you very much.
Restarting the pulse service seems to have worked.
Posting my pulse config files for further troubleshooting. Please let me know if more information is needed.

**client.conf:**

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

; autospawn = yes
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no

**daemon.conf:**


; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; local-server-type = user
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
; default-script-file = /etc/pulse/default.pa

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

; enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
; deferred-volume-extra-delay-usec = 0

---

### Post by prshah on 2012-05-06
> **Zogzog said:**
> Restarting the pulse service seems to have worked.


Your pulse config files seem to be untouched defaults, so no issues there, I think. (unless you can recall some changes you had made earlier to these files, which the upgrade overwrote/replaced).

Please also post your /etc/pulse/*.pa files (default.pa, system.pa)

---

### Post by Zogzog on 2012-05-06
You are right PRShah, I did not make any changes to these files (at least not that I know of).
Posting my .pa files

**default.pa:**

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

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
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
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect
.endif

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
.nofail
load-module module-jackdbus-detect
.fail
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

### Load the RTP receiver module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 sink_properties="device.description='RTP Multicast Sink'"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
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
.ifexists module-console-kit.so
load-module module-console-kit
.endif

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
#load-module module-cork-music-on-phone

### Modules to allow autoloading of filters (such as echo cancellation)
### on demand. module-filter-heuristics tries to determine what filters
### make sense, and module-filter-apply does the heavy-lifting of
### loading modules and rerouting streams.
load-module module-filter-heuristics
load-module module-filter-apply

### Load DBus protocol
#.ifexists module-dbus-protocol.so
#load-module module-dbus-protocol
#.endif

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

load-module module-switch-on-port-available

### Make some devices default
#set-default-sink output
#set-default-source input

**system.pa:**

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

# This startup script is used only if PulseAudio is started in system
# mode.

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Automatically restore the volume of streams and devices
load-module module-stream-restore
load-module module-device-restore

### Automatically restore the default sink/source when changed by the user
### during runtime
### NOTE: This should be loaded as early as possible so that subsequent modules
### that look up the default sink/source get the right value
load-module module-default-device-restore

.ifexists module-dbus-protocol.so
### If you want to allow TCP connections, set access to "remote" or "local,remote".
load-module module-dbus-protocol access=local
.endif

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Enable positioned event sounds
load-module module-position-event-sounds

---

### Post by ldcdc on 2012-05-06
I've been struggling with an issue like this in Ubuntu 12.04. I didn't have the problem from the very beginning, so I had to assume it was either recent software upgrade or something I did.

I think it was something I did: I have wired and wireless networking, and I've played with wireless just for testing purposes. It would appear I left it enabled. Disabling Wireless on my HP laptop stopped the sound stuttering.

My problem seemed to be gstreamer related - smplayer worked fine with wireless enabled, but rhythmbox and clementine didn't.

Anyway, I just thought I would share my experience.

You might want to try the suggestions at [https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling) if wireless is not the problem in your case.

---

### Post by prshah on 2012-05-07
> **Zogzog said:**
> 
Posting my .pa files

Well, your .pa files are also unchanged.

there may be something in the local config (~/.pulse) that is causing the issue. To check, you can do the following:```

mv ~/.pulse ~/dotpulse
sudo service pulseaudio restart
```

This will create a fresh local config. Please check if the issue persists. If sound totally stops working, you can restore the original config with```
rm -rf ~/.pulse
mv ~/dotpulse ~/.pulse
sudo service pulseaudio restart
```

If you still get stuttering with a fresh local config, please check for error indications in the debug log```
dmesg|grep -E -i pulse\|snd
```

Please post back with your results.

---

### Post by qwixilver on 2012-05-16
I have had this same problem, after reading this forum post I did some quick troubleshooting on my own and found a solution that seems persistent. 


in client.conf:

; extra-arguments = --log-target=syslog --resample-method=ffmpeg

---

### Post by Zogzog on 2012-05-19
Hi guys,

I've taken the time to try out the suggested solutions and see whether or not the bug reproduces.
Here are my findings so far:

1) What did not work was disabling my wireless nor adding the resample-method=ffmpeg line to client.conf nor using a fresh client.conf.

2) What clearly does work is killing pulseaudio and then restarting it (I use pulseaudio --kill followed by pulseaudio --start).

3) PRShah, for your request here is what I get when typing   dmesg|grep -E -i pulse\|snd:

[   33.264068] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   33.264139] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   33.264178] snd_hda_intel 0000:00:1b.0: setting latency timer to 64

would appreciate further suggestions.
Thank you again.

---

### Post by acronico on 2012-05-21
I think my problem started when I installed GNU Solfege. This ear training application worked for awhile but it then started by doing some static noises. I think that after flash player started skipping even when the video was fully downloaded/cached.
No problem with rythmbox or vlc.

Restarting pulseaudio didn't do it for me, but after following  [lcdc's link]("https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling") I sorted it out replacing
> load-module module-udev-detect
with
> load-module module-udev-detect tsched=0
in
> /etc/pulse/default.pa

---

### Post by ldcdc on 2012-05-21
> **qwixilver said:**
> I have had this same problem, after reading this forum post I did some quick troubleshooting on my own and found a solution that seems persistent. 


in client.conf:

; extra-arguments = --log-target=syslog --resample-method=ffmpeg

My sound was working fine when playing mp3s, but when playing HD video with 5.1 channels downmixed to stereo, sound started crackling up again (just during movie play). 

Changing "resample-method = speex-float-1" to "resample-method=ffmpeg" in daemon.conf seems to have done the trick so far. I had played before with the resample-method setting, and changing it to speex-float-9 just for kicks proved to be too much for my system. The crackling was unbearable.

There are several resampling algorithms to choose from according to [http://linux.die.net/man/5/pulse-daemon.conf](http://linux.die.net/man/5/pulse-daemon.conf).

---

### Post by Grinage on 2013-01-07
I encountered a similar problem.  My situation has to do with the realtec AC'97/ Intel sound card.  There's a solution for it here in the forums somewhere I've seen it in passing, but alas I can't find it now.  For me restarting the pulse audio server works well enough and the fix lasts for awhile it's only after extended periods of high memory or high processor use that the stuttering and chirping starts, and it only happens in streaming sound or video, so as long as I'm doing neither of those things it doesn't upset me too much.

---

### Post by Grinage on 2013-01-25
Just in case anyone is still following this, when I had to do a reinstall of my machine because I foolishly left it vulnerable as root while I wasn't immediately in front of it, a sound server program recommended a 'low-latency' kernel.  Since I was reinstalling anyway I tried it, and the sound stuttering has not returned.  However, I can't attribute that to just the kernel yet, if the stuttering never returns I'll update the forum.

---

### Post by Grinage on 2013-02-01
stuttering returned, not as prevalent with new kernel.  came upon a problem with stuttering in MSWindows with the same type of Realtek card and their solution was either A replace the CPU or B set the process to use only a single core in a multicore CPU.  Not sure if this is related to linux in any shape form or fashion but the more information the closer a permanent solution gets.

Link to forum with Windows Problems with Stuttering.

[http://www.tomshardware.com/forum/19416-63-realtek-high-definition-audio-causing-video-audio-stuttering](http://www.tomshardware.com/forum/19416-63-realtek-high-definition-audio-causing-video-audio-stuttering)

---

### Post by sciguy125 on 2013-02-01
OP seems to be having the same problem as many others (as well as myself).  There's something wrong with the way Chrome's version of flash interacts with PulseAudio.  It causes flash video to play faster than normal.  Depending on what you're watching, the stuttering audio is more apparent than the messed up video.

The common solution is to disable Chrome's version of flash and install Adobe's.  It works for me, but in principle, I don't like it because it doesn't actually fix the problem, it just works around it.

There's currently a debug going on here:
[http://code.google.com/p/chromium/issues/detail?id=116435](http://code.google.com/p/chromium/issues/detail?id=116435)

---

### Post by Grinage on 2013-02-01
> **sciguy125 said:**
> OP seems to be having the same problem as many others (as well as myself).  There's something wrong with the way Chrome's version of flash interacts with PulseAudio.  It causes flash video to play faster than normal.  Depending on what you're watching, the stuttering audio is more apparent than the messed up video.


happens with firefox, and with various media players and content it seems to be something more extensive than just flash.  From what I've observed with my own issue and from what others have posted is that immediately after a high mem or cpu usage by something, anything, the sound begins to stutter, if you kill pulse audio and bring it back the problem goes away for a time but then returns, and for some people various fixes and work-arounds work, and for some they are still suffering with it, for me using the low-latency kernel reduced the problem and made it less noticeable but it didn't go away entirely.

Some other posters in other threads on this subject have made reference to a particular build in sound card, most of them seem to be related to intel chipsets such as

product: NM10/ICH7 Family High Definition Audio Controller [8086:27D8]
    driver: snd_hda_intel
    latency: 0

in my case.  In Windows this shows up as a Realtek Audio Card, killed windows long ago so not sure which one exactly anymore.  I'm hoping if enough information is collected in one place a permanent solution might be found.

---

### Post by qzjul on 2013-06-17
> **qwixilver said:**
> I have had this same problem, after reading this forum post I did some quick troubleshooting on my own and found a solution that seems persistent. 


in client.conf:

; extra-arguments = --log-target=syslog --resample-method=ffmpeg

Thank you very much, I've been trying dozens of different solutions, but this is the only one that worked! :D

---


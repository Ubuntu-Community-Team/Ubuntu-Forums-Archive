---
title: "HDMI and audio"
date: 2011-07-30
forum: Multimedia Software
---

### Post by MasamuneX on 2011-07-30
Seems to be a lot of these threads going around but nothing seems to match exactly what problems I'm having...

Hardware: MSI G41M-P23 mobo
Galaxy GT 430 GPU w/HDMI
32-bit 11.04 Ubuntu

Sound is supposed to be getting piped through the GPU.  I can get speaker sound from my reciever but ubuntu seems to be completely ignoring the subwoofer that is attached.  I'm using the Sony HT-CT100 reciever/sound bar combo.  The sub is the reciever and the sound bar supports up to 5.1 surround (simulated of course).

I followed all the instructions [at this thread]("http://ubuntuforums.org/showthread.php?t=1668173") and that got me to 2.0 sound.  As I've said though, the sub is being almost completely excluded from this equation.  

Alsa information here:
[http://www.alsa-project.org/db/?f=d4271622da9cd92620ebb088af9ff88560322492](http://www.alsa-project.org/db/?f=d4271622da9cd92620ebb088af9ff88560322492)

My asound.conf file looks like this:
[PHP]
##defaults.ctl.card 1
##defaults.pcm.card 1
##defaults.timer.card 1

pcm.!default {
type hw
card 1
device 8
}
ctl.!default {
type hw
card 1
}[/PHP]

Not sure what more information you guys want, just let me know and I'll post it up.  Thanks!

**EDIT**

Should also mention, in my sound preferences, while GF108 High Definition Audio Controller selected, when I go to output I have two options, Stereo and Surround 5.1.  If I select 5.1 I get no sound whatsoever.  If I select stereo I get sound from the speakers but not sub.  I guess that would explain why I'm not getting sound from the sub.  So I guess the question now is how come 5.1 doesn't send sound out?

---

### Post by BicyclerBoy on 2011-07-30
This is the ELD info for your attached device.
The Sony thing's specs states it is meant to support matrix 5.1 (AC3 DTS) & LPCM 5.1.
The ELD data seems to agree.


[   14.628884] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1 [   14.636004] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1 [   15.404009] HDMI: detected monitor SONY AVAMP [   15.404011]    at connection type HDMI [   15.404014] HDMI: available speakers: FL/FR LFE FC RL/RR RC RLC/RRC [   15.404017] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24 [   15.404020] HDMI: supports coding type LPCM: channels = 6, rates = 44100 48000 88200, bits = 16 20 24 [   15.404022] HDMI: supports coding type LPCM: channels = 8, rates = 44100 48000 88200, bits = 16 20 24 [   15.404025] HDMI: supports coding type AC-3: channels = 6, rates = 44100 48000 88200, max bitrate = 680000 [   15.404027] HDMI: supports coding type DTS: channels = 6, rates = 44100 48000 88200, max bitrate = 1536000


Can you try
speaker-test -D hw:1,9 -r 48000 -c 6

What did you stick in the /etc/pulse/default.pa file ?
You can only have one alsa sink due to limitations in pulseaudio.

---

### Post by MasamuneX on 2011-07-30
> **BicyclerBoy said:**
> 
Can you try
speaker-test -D hw:1,9 -r 48000 -c 6

What did you stick in the /etc/pulse/default.pa file ?
You can only have one alsa sink due to limitations in pulseaudio.

Speaker test runs successfully, I hear sound from 5 directions and one at a low tone which I am guessing is supposed to be my sub.  Finish time was usually just barely shy of 18 seconds.

My defult.pa file is, well, mostly default except for one line which I added following that thread I linked earlier

[PHP]#!/usr/bin/pulseaudio -nF
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
### these drivers manually, but instead use module-udev-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
load-module module-alsa-sink device=hw:1,9
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

### Automatically connect sink and source if JACK server is present
.ifexists module-jackdbus-detect.so
load-module module-jackdbus-detect
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
.ifexists module-zeroconf-discover.so
.nofail
load-module module-zeroconf-discover
.fail
.endif
.ifexists module-raop-discover.so
.nofail
load-module module-raop-discover
.fail
.endif

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
.ifexists module-console-kit.so
load-module module-console-kit
.endif

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
#set-default-source input[/PHP]

More specifically this part:

[PHP]### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-udev-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
load-module module-alsa-sink device=hw:1,9
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink [/PHP]

---

### Post by BicyclerBoy on 2011-07-31
As long as you are not using any snd-hda-intel probemask then..
Your pulseaudio setup seems okay.

The alsa device default override (!default) seems incorrect.
Why do you have device 8 ?


Do you want to have up-mixed audio so that 2.0 plays as 5.1 ?

Can you try playing some AC3 audio (DVD) over HDMI ..

---

### Post by MasamuneX on 2011-07-31
Yea I noticed that after I posted and changed the device to 9 instead of 8.

I'll give the DVD a try in the morning and see what happens.

And as far as audio goes, whenever I had my reciever plugged into my laptop (Win 7) via HDMI the sound was dead on perfect.  Bass kicked in when it was supposed to and the like.  Having 5.1 would be nice, but to be honest at this point I would settle for 2.1.

---

### Post by BicyclerBoy on 2011-07-31
The windows sound driver provides a virtual 5.1 device by up-mixing 2.0 .
Alsa can do this.

Your sound-bar device is meant to support LPCM 6 & 8 channel..
Can you find some test tracks of multi-channel audio & then play to the surround 5.1 device ?
There are audio test tracks in mplayer project.

---

### Post by MasamuneX on 2011-07-31
Well it all seemed to go well when I played a test track or two without changing anything.  Same as the test you had me run earlier, I heard 5 distinct directions of sound, though the test track I ran didn't utilize the sub.  I noticed though that when I played the track the "PCM" light on the receiver came on but simultaneously said "2.0 Ch".

One more thing I've discovered, under sound preferences with 5.1 sound selected the speaker test doesn't work.  As in no sounds come out and the "PCM" light on my receiver doesn't come on.

***EDIT***

Well now I feel like a goddamned idiot.  So, again under sound preferences I never noticed there was a Profile choice under the Hardware tab.  I was at digital stereo (HDMI), after checking every single choice I discovered that "Digital Surround 5.1 (HDMI) nr 4 Output would successfully run the speaker test, including the subwoofer.  I also disabled the "Internal Audio" just to be safe.

So with that unexpected ending, I have a new issue crop up (isn't that always the case...).  I hear a very high pitched ringing from the speakers now.  It's almost like someone is ringing a very small, high-pitched bell in time with the sound coming out.  Can't figure out if it corresponds with any particular noise level but it does hurt the ears, let me tell you.  Under XBMC though I can't hear the noise so I guess I can just not play music under the desktop?  Thanks for all your help bicycler!

---

### Post by BicyclerBoy on 2011-08-01
That noise could be a clue..
The gnome desktop (& most apps) sounds use pulse-audio to allow for sharing & mixing etc..

XBMC & MythTV can use alsa directly (not sharing).

Horrible noises can be caused by incorrect sample rates or bad resampling..

Can you determine the XBMC audio settings ?
Could try using pulseaudio with XBMC as a test.

The music player Clementine allows easy selection of audio playback device.
VLC (from cmd line) is not to bad..
vlc --aout alsa --alsa-audio-device spdif
(not sure what your alsa device will be here)
see if you can find test track..
Test-AC3-v2.0.avi

---


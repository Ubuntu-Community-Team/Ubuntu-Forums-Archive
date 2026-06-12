---
title: "Razer Barracuda AC-1 support?"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by derrekito on 2007-04-21
I have been hesitant to install Ubuntu onto my main Desktop because of the lack of driver support for this sound card.  Anyone have any updated information pertaining to  OSS or ALSA.  I do know that the company C-Media (chipset manufacturer) does not plan on open sourcing their driver (go figure).

it runs on the C-Media 8788 Chipset

---

### Post by derrekito on 2007-04-21
Bump.  This is really the only thing thats keeping me from going full Linux for my Desktop.

---

### Post by derrekito on 2007-04-23
bumps.:popcorn:

---

### Post by joey on 2007-06-17
I have gotten the Razer Barracuda AC-1 running under Feisty.

OSS supports it but ALSA doesn't appear so.  This means tinkering. :-(


1)  Head over to the OSS forums and [install OSS]("http://www.4front-tech.com/forum/viewtopic.php?t=1438") for Ubuntu.

2)  Reboot. You should get the restricted drivers menu with lots of new sound drivers. 

3)  Test your sound in the terminal by using OSSTEST. It should show up  as PCM1  (SPDIF). OSSINFO is another good tool.

4) Use OSSXMIX to set the sound profiles.  Note that  the gnome  sound applet doesn't support the device so it's of no help.

More to come.  esd uses emulated OSS (it was compiled for alsa) so of course that means no OS Sound. I'm trying pulseaudio to see if that works.

Joey

---

### Post by joey on 2007-06-17
Success. Pulse Audio worked! :-) 

1) Follow Paul Bett's easy setup [instructions]("http://blog.paulbetts.org/index.php/2007/04/15/pulseaudio-in-ubuntu-feisty-play-sound-over-the-network")  Note you can also get the flashplugin [here]("http://pulseaudio.vdbonline.net/").
2) Also install libao-pulse libgstreamer-plugins-pulse-0.10 pavucontrol
3) Maybe: edit /etc/libao.conf and change it to "default_driver=pulse". I don't think this is necessary so you might skip this and see if you have any issues.
4) Maybe: sudo ln -sf /usr/bin/esdcompat /usr/bin/esd  (autostarts pulse in gnome but it may not be needed since I have you autostart the daemon below)
5) gconftool -t string --set /system/gstreamer/0.10/default/audiosink pulsesink
6) gconftool -t string --set /system/gstreamer/0.10/default/audiosrc pulsesrc
7) Use this config for /etc/pulse/default.pa   (hal isn't smart enough, mmap is off, etc.)
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


### Load audio drivers statically
#load-module module-alsa-sink
#load-module module-alsa-source device=plughw:1,0
load-module module-oss device="/dev/dsp1" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

#.ifexists /usr/lib/pulse-0.9/modules/module-hal-detect.so

### Automatically load driver modules depending on the hardware available
#load-module module-hal-detect

#.else

### Alternatively use the static hardware detection module (for systems that
### lack HAL support
#load-module module-detect

#.endif

### Load audio drivers automatically on access
add-autoload-sink output module-oss device="/dev/dsp1" sink_name=output source_name=input
add-autoload-source input module-oss device="/dev/dsp1" sink_name=output source_name=input
#add-autoload-sink output module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#add-autoload-source input module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#add-autoload-sink output module-alsa-sink sink_name=output
#add-autoload-source input module-alsa-source source_name=input

.ifexists /usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so

### Load esound protocol
load-module module-esound-protocol-unix

.endif

### Load native protocol
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

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make some devices default
#set-default-sink output
#set-default-source input

.nofail

### Load something to the sample cache
load-sample x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-dir-lazy /usr/share/sounds/*.wav

### Load X11 bell module
load-module module-x11-bell sample=x11-bell

### Publish connection data in the X11 root window
load-module module-x11-publish

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
load-module module-gconf

```8) edit /etc/default/pulseaudio  and set PULSEAUDIO_SYSTEM_START=1
9) reboot 
10) From Apps-Sound menu launch Pulse Audio Device Chooser  which doubles as your new volume applet. ;-)
11) Buy me a beer at UDS :-) 

Joye

---

### Post by derrekito on 2007-06-17
NO WAY! I'm all excited now!  I'm going to have to try it when I get the card back.  It crapped out on me and I had to RMA it.  thank you!

---

### Post by joey on 2007-06-20
I had followed the instructions on how to build libflashsupport myself but couldn't get audio.  This fix was very simple.

Change this in /etc/firefox/firefoxrc

FIREFOX_DSP="padsp"

---

### Post by derrekito on 2007-06-23
Still no sound.  also I get an error from the PulseAudio Applet stating : Connection failed: Connnection refused


what did I mess up on?

Also on the flash part, is there a 64-bit varient of that library file?
Also I couldnt find libgstreamer-plugins-pulse-.10 so I just installed the main plugin file for ligstreamer.

---

### Post by derrekito on 2007-07-13
bump

---

### Post by joey on 2007-07-13
> **derrekito said:**
> Still no sound.  also I get an error from the PulseAudio Applet stating : Connection failed: Connnection refused


what did I mess up on?

Also on the flash part, is there a 64-bit varient of that library file?
Also I couldnt find libgstreamer-plugins-pulse-.10 so I just installed the main plugin file for ligstreamer.


Try [https://answers.launchpad.net/ubuntu/+question/3735](https://answers.launchpad.net/ubuntu/+question/3735) as a possible solution. I had to tinker a bit to make mine work at first as describe above.

No 64 bit that I'm aware of. Google might has some other answers.

typo on lib. Should be libgstreamer-plugins-pulse-0.10

---

### Post by derrekito on 2007-07-14
turns out I had that lib file installed.  The link simply sent me to thread talking about flash audio as well as audio in VLC.  Hrm... my guess is im SOL with 64-bit?

---

### Post by joey on 2007-07-17
If you can't install and get the tests working for OSS with the deb file then there isn't much hope unless you want to compile the OSS system yourself. You could try asking over on the OSS site about it.

---

### Post by derrekito on 2007-07-17
Yeah I decided to sell the Sound card and headphones to my cousin on the cheap... even though they are brand new :(.  Thanks anyways!

---

### Post by joey on 2007-09-01
This now works in Gutsy but requires oss-linux_v4.0-1006_i368.deb or later available from opensound.  

If you get a permission denied when connecting, don't forget to update the pulse-access group so it has your userid.

---

### Post by derrekito on 2007-09-01
> **Rinchen said:**
> This now works in Gutsy but requires oss-linux_v4.0-1006_i368.deb or later available from opensound.  

If you get a permission denied when connecting, don't forget to update the pulse-access group so it has your userid.

64-bit version?

---

### Post by derrekito on 2007-09-01
im installing it right now... wish me luck...

---

### Post by derrekito on 2007-09-01
The device now shows up under sound from the system menu, however I cannot get sound out of it.  OSS is selected and the media chipset is also selected.  trying out the test sounds I get a resource is not ready error.

---

### Post by ravencoder on 2008-06-18
hi i know this is a bit late .. but since 12 september it worx awesomely :)

[http://www.phoronix.com/scan.php?page=article&item=834&num=1](http://www.phoronix.com/scan.php?page=article&item=834&num=1)

check that out the new alsa drivers ALSA 1.0.15-rc1 now supports the AC-1 .. i also have it and it worx for me ;P

---


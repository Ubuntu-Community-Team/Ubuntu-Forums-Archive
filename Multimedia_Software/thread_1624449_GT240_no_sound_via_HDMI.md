---
title: "GT240 no sound via HDMI"
date: 2010-11-17
forum: Multimedia Software
---

### Post by ean5533 on 2010-11-17
I'm having a bit of trouble getting sound to work over HDMI with my GT240 card. I'm running Ubuntu 10.10 (upgraded from 10.04) on kernel 2.6.35-23.

I **can** get sound over HDMI by using the following commands:

```
speaker-test c2 -D plughw:0,7
```
```
aplay -Dplughw:0,7 track06.mp3
```

However, I get no sound from normal applications (Totem, Rhythmbox, flash, etc). It's also worth noting that I can get sound from plughw:0,7, plughw:0,8 and plughw:0,9, but if I use plughw:0,3 there's no sound. I checked in alsamixer and all four channels are unmuted.

I followed the instructions on [this guide]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240") to get this far.

Output of aplay -l and aplay -L:
```
ean5533@ean5533-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ean5533@ean5533-htpc:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Hardware device with all software conversions

```

---

### Post by efflandt on 2010-11-18
For my GT 220 I created the following **/etc/modprobe.d/sound.conf**:

```
#options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2
options snd-hda-intel enable_msi=0 probe_mask=1,2
```The first commented out line was a catch all that worked, but resulted in some errors checking for wrong codecs (dmesg | grep -i hda).  The second line that I am using now cleaned that up.  However, my analog sound card is card 0 and NVIDIA is card 1, so you might try probe_mask=2,1 or probe_mask=0xfff2,0xffff or omit comma and 2nd number if you only want HDMI sound (ie, try probe_mask=0xfff2 or probe_mask=2).  I am not really sure what you need to do when card order is reversed, or if your card 0 device 3 does not work if your card 1 device 0 does not work (does your analog sound work?).

Some apps like flash tend to use whatever is the default sound in alsamixer instead of Sound Preferences (pulse).  So I also created the following **/etc/asound.conf**, so Sound Preferences could select ether analog (2.1 PC speakers) or HDMI sound, and everything would follow along:
```
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
```But like I said, my cards are in a different order.  So after setting this up, **aplay -l** for me shows the following and either analog or HDMI sound work according to device selected in Sound Preferences > Hardware:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by ean5533 on 2010-11-18
If I put this into my /etc/modprobe.d/asound.conf...

```
options snd-hda-intel enable_msi=0 probe_mask=2
```

...then this is what comes out of aplay -l:

```
ean5533@ean5533-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Since we determined earlier that device 3 doesn't seem to produce sound on my machine, it looks like I need to modify my probe mask to instead select device 7. However, I can't seem to pick the right mask! I tried half a dozen different ones, but none worked and I can't find any documentation on what that mask actually represents so I can pick the right one. Any ideas on how to write it? Also, is there a faster way to reload (and test) the sound system than rebooting?

---

### Post by ean5533 on 2010-11-18
Ah HA! Problem solved. I couldn't ever find the right probe_mask value, but instead I added this to my **/etc/pulse/default.pa** file:

```
load-module module-alsa-sink device=hw:1,7
```

That added the necessary output to the normal Sound control panel and I was able to select it there. Boom, done.

A few notes for anyone who reads this thread:

[LIST=1]
[*]In the end, the root problem was my HDMI device #3 didn't produce sound. Don't know why, but it doesn't matter because now I'm using device #7 instead.
[*]I don't know yet whether I can do 5.1 or just stereo -- I'll try to report back on that when I can.
[*]The reason that my sound devices were "reversed" -- that is, the reason that my HDMI was #0 and my Intel sound was #1 -- was because I originally had the following line in my **/etc/modprobe.d/sound.conf**:
```
options snd-hda-intel enable_msi=0 index=1
```
That index=1 option told the system to load HDMI first, as #0. After removing that option, HDMI was loaded as #1 and I was back in line with the rest of the world.
[*]After all this messing around with probe_masks, **alsamixer** apparently re-muted devices 7, 8, and 9, so I had to re-un-mute them before sound worked again.
[*]**efflandt** was quite correct about flash and other programs not playing nice with sound. I didn't have sound working in ALL programs until I added the lines (s)he suggested to **/etc/asound.conf**. (Thanks!)
[*]Here was the final contents of all relevant files on my system when sound started working:
```
**ean5533@ean5533-htpc:~$ cat /etc/modprobe.d/sound.conf** 
options snd-hda-intel enable_msi=0
**ean5533@ean5533-htpc:~$ cat /etc/asound.conf** 
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
**ean5533@ean5533-htpc:~$ cat /etc/pulse/default.pa **
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
load-module module-alsa-sink device=hw:1,7

```
[/LIST]

---

### Post by ean5533 on 2010-11-18
Confirmed 5.1 sound coming over HDMI. Thanks again for the help.

---

### Post by makinmolecules on 2011-02-18
> **ean5533 said:**
> 
[snip]
A few notes for anyone who reads this thread:

[LIST=1]
[*]In the end, the root problem was my HDMI device #3 didn't produce sound. Don't know why, but it doesn't matter because now I'm using device #7 instead.
[/LIST]
 Just a "me-too" to underscore this point in case others are running into a similar problem.  My card is a Gigabyte GT240 GV-N240D3 1GB  and device 3 absolutely refuses to work, even with editing /etc/modprobe.d/sound.conf and adjusting the probemask to get down to one device.  After many forceful applications of my head to a nearby wall, and finding this thread, I found the way I have sound is to NOT use the probemask and use device 0,7 (I have the built-in MB GPU disabled).

Thanks!

---


---
title: "ALSA Mixer &quot;GUI&quot; vs Command line"
date: 2014-12-08
forum: Multimedia Software
---

### Post by daniel225 on 2014-12-08
I've got a generic USB sound card, that works well enough, but I'm seeing some strange behaviour with alsamixer vs amixer.

Alsamixer shows all the channels as below:
[IMG]http://i.imgur.com/MoDDkPZ.png[/IMG]

And I can use

```
amixer -c 1 sset Speaker,0 66%,66%,front
```

to set the volume of the front channel, but rear/center/woofer as in the manpage have no effect. I can still set these voulmes no problem in alsamixer but I need to be able to do them via the command line...

The fact that amixer doesn't return anything at all if you have an error is not helpful!

Basically I just need the ability to output from MPD to front/rear/center and then control the volume individually per channel.

aplay -L
```
root@mediaplayer:~# aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
sysdefault:CARD=Intel
    HDA Intel, AD1984 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=2
    HDA Intel, AD1984 Alt Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=2
    HDA Intel, AD1984 Alt Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=2
    HDA Intel, AD1984 Alt Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, AD1984 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=2
    HDA Intel, AD1984 Alt Analog
    Hardware device with all software conversions
sysdefault:CARD=Device
    USB Sound Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct sample mixing device
dsnoop:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct sample snooping device
hw:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Device,DEV=0
    USB Sound Device, USB Audio
    Hardware device with all software conversions

```

 amixer -c 1 sget Speaker,0

```
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 0 - 197
  Mono:
  Front Left: Playback 131 [66%] [-12.38dB] [on]
  Front Right: Playback 131 [66%] [-12.38dB] [on]
  Rear Left: Playback 130 [66%] [-12.56dB] [on]
  Rear Right: Playback 128 [65%] [-12.94dB] [on]
  Front Center: Playback 6 [3%] [-35.81dB] [on]
  Woofer: Playback 6 [3%] [-35.81dB] [on]
  Side Left: Playback 6 [3%] [-35.81dB] [on]
  Side Right: Playback 6 [3%] [-35.81dB] [on]

```

---

### Post by tgalati4 on 2014-12-08
*amixer* was written in 2000.  *alsamixer* was written in 2009.  You can write a script using the *tee* command to send commands to *alsmamixer* to simulate a commandline sound control.  

You can also use commandline control with pulseaudio:

[http://ubuntuforums.org/showthread.php?t=1132200](http://ubuntuforums.org/showthread.php?t=1132200)

[https://bbs.archlinux.org/viewtopic.php?id=124513](https://bbs.archlinux.org/viewtopic.php?id=124513)

---


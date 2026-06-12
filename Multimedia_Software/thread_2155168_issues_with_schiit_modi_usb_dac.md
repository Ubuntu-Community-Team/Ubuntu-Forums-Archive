---
title: "issues with schiit modi usb dac"
date: 2013-06-17
forum: Multimedia Software
---

### Post by thrill0gy on 2013-06-17
hey guys. i recently picked myself up a schiit magni and modi, and have been having issues with getting the modi to run. both pulse and alsa seem to have issues allowing me to use it, but alsa recognizes it:

```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Device
    Schiit USB Audio Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```

but the PCM channel in alsamixer is showing 00, and i can't change it at all. when i spoke to a gentleman from schiit he said that he had it running on 13.04 fine, so there -is- a way to get it running. any ideas?

currently running ubuntu 12.04 lts x64

update: dac works fine out of the box on my 13.04 laptop, but my 12.04 lts workstation shows dummy output only.

---

### Post by bionnaki on 2013-07-06
Any progress getting the Modi to work? I have the same issue. 

> **thrill0gy said:**
> hey guys. i recently picked myself up a schiit magni and modi, and have been having issues with getting the modi to run. both pulse and alsa seem to have issues allowing me to use it, but alsa recognizes it:

```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Device
    Schiit USB Audio Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    Schiit USB Audio Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```

but the PCM channel in alsamixer is showing 00, and i can't change it at all. when i spoke to a gentleman from schiit he said that he had it running on 13.04 fine, so there -is- a way to get it running. any ideas?

currently running ubuntu 12.04 lts x64

update: dac works fine out of the box on my 13.04 laptop, but my 12.04 lts workstation shows dummy output only.

---

### Post by daniel139 on 2014-04-09
I'm also having the same issue.  Anyone? :(

---


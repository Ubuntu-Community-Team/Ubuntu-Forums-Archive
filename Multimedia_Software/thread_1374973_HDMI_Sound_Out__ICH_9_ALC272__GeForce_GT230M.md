---
title: "HDMI Sound Out | ICH 9 ALC272 | GeForce GT230M"
date: 2010-01-07
forum: Multimedia Software
---

### Post by cajual on 2010-01-07
So I have been posting most of my concerns in the Hardware & Laptop forum, and regardless how much I have helped others, I have yet to receive a single post in return.  So I turn to this forum, since I see so many willing to help here in contrast.

**The Problem**
I have a Toshiba a505 Laptop with an ICH9 chipset, an nVidia GT230M, and an HDMI out port.  I can not, for the life of me, configure the HDMI sound to work with my TV (which accepts HDMI sound).  I have tried too many things to denote in this single post, but if anyone has any idea's, I will let you know if I have tried them.

I have tried forcing snd-hda-codecs-intelhdmi/nvhdmi through modprobe, and set them up in modules configuration.  I have tried setting alsa-base.conf model=toshiba, enable_msi=1, position_fix=1, etc...  The problem is not my sound though, it is just my HDMI out.  Speaker-test gives no errors when I try the digital out, but it doesn't output any sound either.  I do not have an HDMI device, and when I open ALSAMIXER, my nVidia Card shows up as: *NVidia Card ID a - This device has no options.*

UPDATE:

> 
Just ran the alsa-info tool:

[http://www.alsa-project.org/db/?f=bc5845c00bd5a2a2d28eef5838773c21371756b0](http://www.alsa-project.org/db/?f=bc5845c00bd5a2a2d28eef5838773c21371756b0)

Can anyone discern why I have no snd-*hdmi* module loaded?
```

cajual@cajual-laptop ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

cajual@cajual-laptop ~ $ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC272 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```Everything is unmuted in **alsamixer** and I have tried every variation in the sound setup that is possible (from Analog to Digital). As far as I can tell, my HDMI port is through the nVidia graphics controller, and in **sysinfo** (from the synaptic package manager) nVidia shows up as the sound controller, but Ubuntu or Alsa forces it all through Intel. Something is amiss and I just can't figure it out.

Any advice?

PS: It is an nVidia GT 230M.

---

### Post by jeanfou on 2010-01-12
Same cards (GeForce GT230M and ICH9ALC272) and same issue...:(

---


---
title: "ALSA not working with Pulseaudio via SPDIF"
date: 2008-08-23
forum: Mythbuntu
---

### Post by pnauta on 2008-08-23
Hi,

My HW: Asrock N7F-HDReady, SPDIF header connector is connected to a Sony Receiver, and the hardware setup has been proven to work in the past.

Software setup and tests:
MythBuntu 8.04 / 0.21.  Installation was originally 7.10 Mythbuntu.
Nvidia 173.14.12 driver on board, used envyng to install.
Additional packages that were installed at some point, that may have an influence and may have caused Pulseaudio to be configured (at which point Mythmusic stopped working) are motion (to watch the cats in my living room during night), Rosegarden for my :guitar: daughter's USB / Midi Yamaha keboard, audacity, Xine.

> # alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

 > aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

What's really worrying me is the output from apay -L which shows no line with digital:
>  aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
Myth setup: ALSA:default in general, ALSA:default in Mythmusic.
I checked if ALSA:pulse works but no luck at all.
What is working: Mythstreams
What is not working: sound on any other component of MythTV
Hope this is enough.  Any ideas are welcome. I've seen almost everything written about it but everyone's hardware setup is different, and the information about how it's supposed to be setup is nowhere to be found.  Like: when using Pulseaudio with ALSA, how is it supposed to be setup?  And how do I check Pulse setup and how do I test it?  How can I remove Pulseaudio and restore ALSA to not use it?

Hope someone can help me here, because the WAF is kicking in now, after troubleshooting for some 2 weeks now :mad:

---

### Post by volkswagner on 2008-08-23
Try changing you setup from default to the following syntax in post #4, it worked for me and others.

[http://ubuntuforums.org/showthread.php?t=839883&highlight=ALSA%3Ahw%3A1%2C1]("http://ubuntuforums.org/showthread.php?t=839883&highlight=ALSA%3Ahw%3A1%2C1")

You can get your proper card number and device number for SPDIF by running

```
aplay -l
```

---


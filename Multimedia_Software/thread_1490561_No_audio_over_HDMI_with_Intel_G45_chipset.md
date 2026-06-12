---
title: "No audio over HDMI with Intel G45 chipset"
date: 2010-05-22
forum: Multimedia Software
---

### Post by CmdrJudas on 2010-05-22
Hi,

I'm trying to set up a new HTPC and can't get sound to work over HDMI.  If I set System > Preferences > Sound > Hardware and set the profile to Analog Stereo Duplex, I get sound from the speaker port just fine.  However if I set the profile to Digital Stereo (HDMI) Output I get nothing on my TV.  I'm using 10.04 LTS.  Any help would be much appreciated.

Some data:

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```

$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI
    HDMI Audio Output

```

alsamixer looks ok: I get Master, PCM and S/PDIF channels.  The former two are set high, and S/PDIF is shows "00" on a green background, which I presume means it's unmuted.

Any thoughts?

---

### Post by CmdrJudas on 2010-05-23
Minor update: I rummaged in the BIOS and changed my SPDIF OUT Mode from SPDIF to HDMI, but still no audio coming out of my TV.

---

### Post by CmdrJudas on 2010-05-29
SOLVED: I was using ALSA version 1.0.21.  Upgrading to 1.0.23 using the script here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) solved everything.

```
$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

---


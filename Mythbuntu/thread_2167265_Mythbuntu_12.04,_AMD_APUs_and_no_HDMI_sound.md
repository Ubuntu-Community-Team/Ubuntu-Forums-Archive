---
title: "Mythbuntu 12.04, AMD APUs and no HDMI sound?"
date: 2013-08-13
forum: Mythbuntu
---

### Post by Pierre_duParte on 2013-08-13
As per the topic, is this the new standard? I have just invested in an AMD A8 6600 APU rig. After the usual stuffing about sorting HDMI video out, I had no sound over HDMI. Another day spent googling and reading and de-obfuscating the jargon, it seems as if we cannot do sound over HDMI anymore.

Is this correct, or has some one found a way?

Thanks

---

### Post by jrocor on 2013-08-20
Are you talking about no sound coming through the HDMI when watching TV or a movie in the frontend?

---

### Post by Pierre_duParte on 2013-08-20
> **jrocor said:**
> Are you talking about no sound coming through the HDMI when watching TV or a movie in the frontend?

Hi,
Sorry for the delay in getting back here... there is no HDMI option in the sound hardware selections. I've managed to get SPDIF working, which will do.

Nevertheless, getting sound over hdmi would be one less cable...

thanks

---

### Post by larsolav on 2013-08-21
What do the commands
   aplay -L
   aplay -l 
give you in termininal?

---

### Post by Pierre_duParte on 2013-08-21
> **larsolav said:**
> What do the commands
   aplay -L
   aplay -l 
give you in termininal?

I should know these off by heart by now ;)

```
aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Generic
    HD-Audio Generic, ALC898 Analog
    Default Audio Device
front:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    Front speakers
surround40:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    Direct sample mixing device
dmix:CARD=Generic,DEV=1
    HD-Audio Generic, ALC898 Digital
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    Direct sample snooping device
dsnoop:CARD=Generic,DEV=1
    HD-Audio Generic, ALC898 Digital
    Direct sample snooping device
hw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    Direct hardware device without any conversions
hw:CARD=Generic,DEV=1
    HD-Audio Generic, ALC898 Digital
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=0
    HD-Audio Generic, ALC898 Analog
    Hardware device with all software conversions
plughw:CARD=Generic,DEV=1
    HD-Audio Generic, ALC898 Digital
    Hardware device with all software conversions

``` 


As stated before, I managed to get the following device to work after a  bit stuffing about and turning on on-board audio in the BIOS:
aplay -l
```
ice #0: subdevice #0
card 0: Generic [HD-Audio Generic], device 1: ALC898 Digital [ALC898 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Would I be right in thinking that the HDMI sound should come from the AMD APU (A8)?


Thanks for your interest....

---


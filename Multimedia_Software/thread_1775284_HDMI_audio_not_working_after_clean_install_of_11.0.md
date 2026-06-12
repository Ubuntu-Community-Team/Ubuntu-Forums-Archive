---
title: "HDMI audio not working after clean install of 11.04"
date: 2011-06-04
forum: Multimedia Software
---

### Post by SpritBille on 2011-06-04
Hey. I had Ubuntu 11.04 installed from an update from 10.10 and then HDMI audio worked.

But after I made a clean install of 11.04 the HDMI audio is missing. What to do?

I hvad posted some things I can see in other posts that you could use. BTW sound works with my headphones.

Thank you all.

```
bille@bille-MS-7255:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    Front speakers
surround40:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Digital
    HDMI Audio Output
dmix:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    Direct sample mixing device
dmix:CARD=VT82xx,DEV=3
    HDA VIA VT82xx, ALC888 Digital
    Direct sample mixing device
dsnoop:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=VT82xx,DEV=3
    HDA VIA VT82xx, ALC888 Digital
    Direct sample snooping device
hw:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=VT82xx,DEV=3
    HDA VIA VT82xx, ALC888 Digital
    Direct hardware device without any conversions
plughw:CARD=VT82xx,DEV=0
    HDA VIA VT82xx, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=VT82xx,DEV=3
    HDA VIA VT82xx, ALC888 Digital
    Hardware device with all software conversions
```

```
bille@bille-MS-7255:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 3: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---


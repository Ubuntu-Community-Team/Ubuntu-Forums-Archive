---
title: "Trying to add a device to asound.conf"
date: 2011-05-15
forum: Multimedia Software
---

### Post by Twizzle on 2011-05-15
I have Ubuntu 10.10 x64 server installed and currently have it running XBMC linked to my TV with an HDMI cable. Sound and video work fine.

I have just installed forked-daapd and was planning on connecting the onboard sound card to my stereo with an analog 3.5mm lead which I can then control with my iPhone 'remote' app.

forked-daapd seems to be running fine and is trying to output the sound to the 'default' device, however I think that this is set up as the HDMI out.

My understanding is that I can add / edit asound.conf to tell forked-daapd where to look, so I think what I am after is a way to add an entry to asound.conf which tells it to play through the analog out.

A few bit from my system:
 aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

aplay -L

```
null
    Discard all samples (playback) or generate zero samples (capture)
default
front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, VT1708B Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, VT1708B Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, VT1708B Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, VT1708B Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions

```

current asound.conf

```
#Tweak for HDMI sound ON
pcm.!default {
  type plug
   slave {
       pcm "hdmi"
   }
}
#Added for analog out
pcm.analog {
        type hw
        card 0
        device 0
}
```


I added the bottom bit for analog out thinking it might work...

---


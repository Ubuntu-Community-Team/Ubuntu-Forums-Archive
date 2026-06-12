---
title: "Speakers don't work"
date: 2010-11-20
forum: Multimedia Software
---

### Post by heiNey on 2010-11-20
Can someone help me with this?

I have a 5.1 surround sound system, and I'm trying to use it with 10.10.  Only 2 of my speakers work when I do the speaker test (front left and front right).  However, when I watch a movie, the center, front left and front right and the subwoofer work.  The 2 rear speakers are very faint and pretty much have no sound.

I am using the analog output from my onboard sound.  I have an HDMI cable from my video card to the TV, but do not have a receiver, so I can't use digital audio.  I disabled the audio from the HDMI and my analog sounds the same.  I'm not sure what I need to do.  I changed the preferences to anything that would let me test the rear speakers and still get nothing.

I have a GIGABYTE GA-965P-DS3 LGA 775 Intel P965 Express ATX Intel Motherboard if that helps.

```



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```



aplay -L
default
pulse
    Playback/recording through the PulseAudio sound server
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
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, ATI HDMI
    Hardware device with all software conversions

```

---


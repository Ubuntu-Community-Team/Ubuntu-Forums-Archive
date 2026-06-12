---
title: "Why is my optical output stereo only?"
date: 2011-07-26
forum: Multimedia Software
---

### Post by ceejay on 2011-07-26
Ubuntu 11.04, with Myth 0.24 and XBMC 10.1.  Hardware is an Asus P8H67-M Pro mobo which I bought specifically because it boasts an optical output, which I need to send 5.1 sound to my receiver.

My plan is to set up MythTV for watching TV, and have it send stereo sound directly to the TV via HDMI. This part is working fine.

And then set up XBMC to play my collection of ripped and recorded video, with the sound always going via optical spdif to the receiver. I did have this working on a prototype (different mobo) but now I have my "final" hardware I can't get this bit to go. 

The issue seems to be that the OS is only seeing the Optical output as a stereo device - for example if I go System Settings - Sound I can see two hardware devices - "Digital Stereo HDMI" and "Digital Stereo Duplex (IEC958)"

I'm new to this area of Linux, so would really appreciate some pointers - I've spent the last couple of hours reading immensely long threads and not getting any wiser!

For starters:
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and

```

$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

I have no .asoundrc or /etc/asound.conf

Can anyone point me where I should go next?

TIA

---

### Post by ceejay on 2011-07-27
Never mind .... turned out to be an XBMC configuration issue - I needed to turn navigation sounds off (!!).

I guess I was misled into thinking it was an OS problem by being told the device was Stereo-only, but I presume that from the POV of the OS that's true.

---

### Post by lkjoel on 2011-07-27
Could you mark this thread as solved? Thread tools->Mark this thread as solved

---

### Post by mutt|ey on 2011-08-04
I have an integrated audio (Realtek ALC892 Audio Codec) on a Asrock 880GXH.

If i set in phonon:

- "Internal Audio" > "Analog Stereo Duplex" i can only hear audio in passthrought (Dolby Digital and DTS)

- "Internal Audio" > "Digital Stero Duplex " i can hear all "normal" sound but no passthrought (Dolby Digital and DTS)

Ubuntu 11.04 32bit, Kernel 2.6.38-11

---


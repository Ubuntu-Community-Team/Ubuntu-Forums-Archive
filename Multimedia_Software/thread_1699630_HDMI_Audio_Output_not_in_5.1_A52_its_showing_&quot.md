---
title: "HDMI Audio Output not in 5.1 A/52 its showing &quot;stereo&quot; How do I Fix?"
date: 2011-03-03
forum: Multimedia Software
---

### Post by kanazky on 2011-03-03
Hey,

**Graphics Card**: 
HD 5730 ATI

**Type**:
Notbook

**Source**:
BluRay MKV - x264 - AC 5.1 and Dolby Digital (Audio)

**Output Attempt**:
HDMI to 5.1 Receiver.

**aplay -l**
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**Player**:
- VLC 1.1.7
- Other options I will try: smPlayer and MPlayer-GUI


The Sound settings in ubuntu is offering me "Stereo" as an output mode, and VLC isn't offering A/52 over spdif or AC 5.1

---

### Post by kanazky on 2011-03-04
Hate to bump my own thread but I have the aplay -L information:

> 
null
Discard all samples (playback) or generate zero samples (capture)
pulse
Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
Front speakers
surround40:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
Direct sample snooping device
hw:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
HDA Intel, STAC92xx Analog
Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
HD-Audio Generic, ATI HDMI
HDMI Audio Output
dmix:CARD=Generic,DEV=3
HD-Audio Generic, ATI HDMI
Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
HD-Audio Generic, ATI HDMI
Direct sample snooping device
hw:CARD=Generic,DEV=3
HD-Audio Generic, ATI HDMI
Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
HD-Audio Generic, ATI HDMI
Hardware device with all software conversions 


The output works fine for Stereo PCM 44hz, I want 5.1 and digital with higher then 44hz PCM audio quality :(

Thanks :D

---


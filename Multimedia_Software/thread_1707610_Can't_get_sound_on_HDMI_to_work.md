---
title: "Can't get sound on HDMI to work"
date: 2011-03-15
forum: Multimedia Software
---

### Post by Wibbe82 on 2011-03-15
Hi, 

I'm having problem to get my sound work on my HTPC based on Asus AT5IONT-I Deluxe motherboard. I can get analogue sound out but not the digital sound on HDMI nor optical. I have tried a couple of things I've found on swedish forums, but nothing have worked so I'm ready to start over again from the beginning. I'm a real beginner when it comes to Ubuntu so step by step instructions is prefered. 

Here's some info:

```
wibbe@HTPC:~$ cat /proc/asound/cards
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xf9ef8000 irq 53
1 [NVidia ]: HDA-Intel - HDA NVidia
HDA NVidia at 0xfbbfc000 irq 19
```
```
wibbe@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0
```
```
wibbe@HTPC:~$ aplay -L
default
pulse
Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
Front speakers
surround40:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
HDA Intel, ALC887 Digital
IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
Direct sample mixing device
dmix:CARD=Intel,DEV=1
HDA Intel, ALC887 Digital
Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
HDA Intel, ALC887 Digital
Direct sample snooping device
hw:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
HDA Intel, ALC887 Digital
Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
HDA Intel, ALC887 Analog
Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
HDA Intel, ALC887 Digital
Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
HDA NVidia, NVIDIA HDMI
HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
HDA NVidia, NVIDIA HDMI
HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
HDA NVidia, NVIDIA HDMI
HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
HDA NVidia, NVIDIA HDMI
HDMI Audio Output
dmix:CARD=NVidia,DEV=3
HDA NVidia, NVIDIA HDMI
Direct sample mixing device
dmix:CARD=NVidia,DEV=7
HDA NVidia, NVIDIA HDMI
Direct sample mixing device
dmix:CARD=NVidia,DEV=8
HDA NVidia, NVIDIA HDMI
Direct sample mixing device
dmix:CARD=NVidia,DEV=9
HDA NVidia, NVIDIA HDMI
Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
HDA NVidia, NVIDIA HDMI
Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
HDA NVidia, NVIDIA HDMI
Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
HDA NVidia, NVIDIA HDMI
Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
HDA NVidia, NVIDIA HDMI
Direct sample snooping device
hw:CARD=NVidia,DEV=3
HDA NVidia, NVIDIA HDMI
Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
HDA NVidia, NVIDIA HDMI
Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
HDA NVidia, NVIDIA HDMI
Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
HDA NVidia, NVIDIA HDMI
Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
HDA NVidia, NVIDIA HDMI
Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
HDA NVidia, NVIDIA HDMI
Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
HDA NVidia, NVIDIA HDMI
Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
HDA NVidia, NVIDIA HDMI
Hardware device with all software conversions
```

---

### Post by iniva on 2011-05-07
Hello,

I am having exactly same problem. I just purchased Asus AT5IONT-I Deluxe motherboard. Seems that I am not getting HDMI Audio to work. I have tried with clean install of Fedora 13 and Uubntu 11.04 and neither will give me audio over HDMI. Analog frontpanel connection is working.

Did you find solution to your problem?

-Ilpo

---

### Post by BicyclerBoy on 2011-05-08
@OP

The optical/Toslink or S/PDIF IEC958 output problem is not likely related to HDMI.
(Digital coaxial cable connection is S/PDIF as well)
 
From terminal run..
speaker-test -D iec958 -c2

Check your amp shows digital 2ch PCM

Force vlc to output direct to IEC958..
 vlc --aout alsa --alsa-audio-device iec958

Play a recording with AC3 sound track (DVD) ...check the AC3 lights come on..

HDMI audio on current gen video cards is via audio devices provided by video driver & video hardware.
So you need recent video drivers & up-to-date alsa 1.0.23 or later in kernel.

I think the very latest pulse-audio is finally able to do/allow digital pass-thru (AC3, DTS)

---


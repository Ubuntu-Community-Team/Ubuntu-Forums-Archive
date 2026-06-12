---
title: "Mythtv HDMI Audio problem"
date: 2011-11-13
forum: Multimedia Software
---

### Post by Tinnum on 2011-11-13
I have MythTV running via Maverick 10.10 with the Asus AT5IONT-1 mobo. All HDMI audio devices function perfectly (with eternal thanks to "Bicycler Boy") with the exception of MythTV which loads the internal audio  sound  by default (very occasionally it will load HDMI stereo). I have trailed through the forums but as a newbie I am not very confident. I am afraid  of corrupting my otherwise stable audio system, but presume there is a way of suppressing the internal analogue audio on startup of Myth TV.
I need to get MythTV to play through HDMI by default

My aplay -l below
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

aplay -L
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



Many thanks in anticipation!

---

### Post by MoreOrLess on 2011-11-13
You have to use MythTV's configuration to set the device you want. See this: [http://www.mythtv.org/wiki/ATI_Radeon_HDMI#MythTV_HDMI_Sound](http://www.mythtv.org/wiki/ATI_Radeon_HDMI#MythTV_HDMI_Sound)
Your HDMI card looks to be hw:1,3

---

### Post by Tinnum on 2011-11-13
Thanks for your reply .... will  persevere

---

### Post by Tinnum on 2011-11-13
Hi MoreorLess,
Believe me I have tried all the front end settings. When audio does work, it works with either Alsa Default or PulseAudio default. I think with Nvidia sound cards there is a problem with the logical ID numbers. I am too much of a newbie to understand Alsa except in its basic form. I have spend days on this problem but am determined not to be defeated althoug I he had to resort to throwing my problem out to the forum......

---

### Post by Tinnum on 2011-11-13
Ok,  I solved the problem (it seems). The /etc/asound.conf file was missing. So i entered
gksudo gedit /etc/asound.conf to produce asound.conf file and pasted in

[I]pcm.!default {
[/I][I] type plug
[/I][I] slave.pcm {
[/I][I] type hw
[/I][I] card 0
[/I][I] device 7
[/I][I] }
[/I][I] }

(The card and device values need to correspond to your hardware).
see

[http://www.mythtv.org/pipermail/mythtv-users/2011-March/311816.html](http://www.mythtv.org/pipermail/mythtv-users/2011-March/311816.html)

Bi
[/I]

---


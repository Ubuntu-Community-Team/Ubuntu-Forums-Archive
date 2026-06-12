---
title: "M-Audio Fast Track Ultra only uses 2 Channels"
date: 2011-11-09
forum: Multimedia Software
---

### Post by abocanegra on 2011-11-09
I am working on a project that requires the use of at least 6 of the 8 channels available to me with the [M-Audio Fast Track Ultra (USB)]("http://www.m-audio.com/products/en_us/FastTrackUltra.html").

Software I am using for the project
[SuperCollider]("http://supercollider.sourceforge.net/") - Audio Ran through Jack
[Sage]("http://www.sagemath.org/")
Python
Arduino

My issue is that I am only able to output through channel 1 and 2, which is all SuperCollider shows as well when I start the server. However, Jack shows all 8 Channels.

I have compiled the latest [ALSA]("http://www.alsa-project.org/main/index.php/Main_Page") in my kernel and can see the M-Audio as a 1-output in my sound preferences as well.

Below is some info.
**-lsusb**
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 0763:2080 Midiman M-Audio RunTime DFU**
Bus 002 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```-cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Nov  8 2011 for kernel 2.6.32-35-generic (SMP).
```-aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[B]card 1: Ultra [Fast Track Ultra], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]

```I am running [UbuntuStudio 10.04 x64]("http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/"). I cannot upgrade to a newer version as Supercollider and Sage do not get along with the latest version yet. I have researched quite a bit and being able to use 2 channels wasn't much work, but not being able to get full use of all 8 channels is of course frustrating. I am willing to buy another USB Audio Adapter with between 6 - 8 output channels if anybody can recommend one that works better within Linux. Windows and Mac are not an option. The spirit of the project is open source and I'd like to stick to that as much as possible (hardware excluded i suppose).

****[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)
This is the site was most useful in helping me compile the latest Alsa, it is of course for an older Ubuntu, but the idea was there and it seemed to work. Maybe I missed something in the translation from Ubuntu 9.10 to 10.04

---

### Post by MoreOrLess on 2011-11-09
This script should help with the latest alsa: 
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by abocanegra on 2011-11-10
Your post was helpful. I have the most up to date alsa. However, this section appears to be where I need help

Multichannel you can test the following way:
1. Type $aplay -L to find out about your pcm device . e.g "surround51"
2. Type $speaker-test -D surround51 -c6
Note: If the channel mapping should be wrong you need to adjust it in .asoundrc

What do I need to adjust in the .asoundrc

---

### Post by abocanegra on 2011-11-10
This is what I a getting from 

aplay -L 
```
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC663 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
front:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    Front speakers
surround40:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    IEC958 (S/PDIF) Digital Audio Output

```

However, I am still unsure how to get it to actually output 7.1 channel (8 outputs). When I attempt it says that 6 channels are inaccessible. I have tried playing with ./asoundrc but have had no luck, admittedly I am inexperienced with alsa.

---

### Post by abocanegra on 2011-11-14
I am still hoping to get somebody to help me set up the m-audio card to utilize all 8 channels.

I followed the directions from [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") to get a more in depth output for you to check out.

[Here is the link to the output.]("http://www.alsa-project.org/db/?f=82c9819a8658db6109749d8eabdeabf83d079477")

---

### Post by abocanegra on 2011-11-16
Solved:
I have only had success with linux-header-2.6.32-33 2.6.32-35 did not work. This may have something to do with the fact that this download (linux-alsa-driver-modules-2.6.32-33-generic) from synaptic helped me out.

Download latest alsa driver/lib/utils
For Each
copy to /usr/src
unpack
./configure
make
make install
reboot
it should be visible now.
You must now run alsamixer and make sure that for each channel only one output channel is unmuted (1-1, 2-2, 3-3 and so on, mute 1-2 1-3 1-4 1-5 1-6 1-7 1-8) It is tedious but it helps.

*********************This only works if you are running the Fast Track Ultra from the external power, not USB. You only get 2 channels with USB.

---


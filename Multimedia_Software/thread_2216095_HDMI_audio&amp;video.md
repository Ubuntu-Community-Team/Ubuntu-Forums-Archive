---
title: "HDMI audio&amp;video"
date: 2014-04-10
forum: Multimedia Software
---

### Post by neitono on 2014-04-10
hey guys im n00b when it comes to linux just started with ubuntu i have pulse audio controller i have the HDMI video and its really shaky and also I have audio plz? T.T

---

### Post by David D. on 2014-04-10
Welcome to the forums.

Please provide some additional information with as much detail as you can.  

Which *buntu are your using (Ubuntu, Kubuntu, etc.)?

Which version do you have installed (12.04, 13.10)?

What video graphics do you have (NVidia, ATI, etc.)?

Describe your problem in more detail.

You will find your fellow *buntu users very helpful here of the forum.

---

### Post by Kirboosy on 2014-04-10
Welcome to the forums! I would advise that you look at this post on how to get your questions answered as quickly as possible

[Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811&viewfull=1#post8920811")

Hope that helps!
~Caboose

---

### Post by neitono on 2014-04-10
I am running ubuntu 12.04 lts 64 bit my computer is an HP 655 E1 AMD vision and my problem is i plug my tv into my laptop threw HDMI I have video and its shaky and blurred it seems like and i have no audio i download pulse audio control and went into video options and switched to to the proper configuration and HDMI is recognized  but when i set it to HDMI out i have no audio threw the TV [h=3][/h]

---

### Post by papibe on 2014-04-10
Hi neitono.

Could you open a terminal, run these commands one by one, and post back the output they generate? (you can copy/paste the text from the terminal):
```
lspci -nnk | grep -iA2 vga

aplay -l

aplay -L
```
Regards.

---

### Post by neitono on 2014-04-10
```
lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7310] [1002:9809]
Subsystem: Hewlett-Packard Company Device [103c:1885]
    Kernel driver in use: radeon

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

aplay -L
Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=Generic_1
    HD-Audio Generic, ALC269VC Analog
    Default Audio Device
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Front speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Hardware device with all software conversions
```

---

### Post by papibe on 2014-04-10
Thanks.

Good news: the hdmi audio devices are there.

Could you run a sound test? Please open a terminal and run this:
```
speaker-test -c2 -Dhdmi -twav
```
You should be able to hear test sounds on your TV.

Let us know if that works.
Regards.

---

### Post by neitono on 2014-04-10
k

---

### Post by neitono on 2014-04-10
ok I ran ```
sudo apt-get install pulseaudio pulseaudio-utils pavucontrol
``` (i ran this when i was using peppermint) and now i have audio on HDMI but my other problem now is that it sounds staticy  and i lost my ability to use to monitors  ```
<aplay -l>= card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
<aplay -L> card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC269VC Analog [ALC269VC Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````

jacob@jacob-HP-655-Notebook-PC:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=Generic_1
    HD-Audio Generic, ALC269VC Analog
    Default Audio Device
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Front speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Hardware device with all software conversions 
```

---

### Post by neitono on 2014-04-15
Bump

---

### Post by papibe on 2014-04-16
Those packages are preinstalled on vanilla Ubuntu. Are you running Ubuntu, Xubuntu, or Lubuntu?

Could you run the speaker test again?
Is it 'staticy' too? 
Does lowering the overall volume on the computer improves the sound quality?

Regards.

---


---
title: "Sandy Bridge HDMI sound output"
date: 2011-05-31
forum: Multimedia Software
---

### Post by drhjort on 2011-05-31
I have only been able to output sound over HDMI when I enter the following into the terminal. ```
aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav
```
How can I output all my audio though card 0 device 7 or the HDMI port? 

My system is composed of an i5-2400, a H67 motherboard and a fresh install of 11.04. Any help is greatly appreciated.

---

### Post by drhjort on 2011-06-01
aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1

```

aplay -L output:
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC889 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC889 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
```

The device I want to use is the plughw:CARD=PCH,DEV=7 as this is the only device that outputs any to my speakers when I use aplay or speaker-test. 

I would really appreciate any help with getting all of the sound through the integrated HDMI port on my motherboard, or at least how to make this situation usable (play sound for music and video).

---

### Post by lidex on 2011-06-03
You need to setup a configuration file telling alsa/pulse to use that device. 
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
[http://alsa.opensrc.org/Main_Page](http://alsa.opensrc.org/Main_Page)

---

### Post by Dan Again on 2011-10-12
I am having the exact same issue - HDMI audio work fine ONLY when I run the command from the first post in a terminal. Can someone offer a little more guidance on how to "setup a configuration file telling alsa/pulse to use [the correct] device"?

Thanks in advance.

---

### Post by Dan Again on 2011-10-12
I can't seem to get this to work.

When I run...

```
aplay -D plughw:0,7 /usr/share/sounds/alsa/Front_Center.wav
```

In terminal, I get good sound.

The result of...

```
aplay -l
```

is...

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I've created an .asoundrc file in my /home folder and tried many variations, but nothing seems to work.

Any suggestions?

---

### Post by BicyclerBoy on 2011-10-12
To get system wide sound over that audio codec you can use pulse audio..
Pulse does not see hw:0,7 only the first (2) devices of each card are enumerated.

So edit your /etc/pulse/default.pa, add this line at the end:
load-module module-alsa-sink device=hw:0,7

Make sure there is only one "load-module module-alsa-sink" device entries..

Now the hw:0,7 device will appear in gnome audio prefs or pavucontrol.

---

### Post by Dan Again on 2011-10-13
Solved! Thank you so much!

---


---
title: "No Audio: Xubuntu 11.04; nVidia audio chipset"
date: 2011-09-04
forum: Multimedia Software
---

### Post by j0rg3 on 2011-09-04
I've Googled myself silly and I just can't figure out how to get audio out of this thing.  


% lspci | grep -i audio
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)

It doesn't recognize any audio hardware.  Evidently, alsa-backports doesn't apply to Natty.  Couldn't find Envy.  Installed "alsa-tools-gui" but it also just couldn't find anything.  /-:

Am I just out of luck?

Thanks!

---

### Post by BicyclerBoy on 2011-09-04
Are you saying that 
aplay -l
aplay -L
shows no audio devices ?

Someone at nVidia must have been a "Tron" fan..
The MCP79/ION chipset audio does seem to work..The setup is bit odd.
ION HDMI audio works with alsa 1.0.22.
As I understand, some MCP79 boards may only output 2 ch PCM over HDMI.

lsmod | grep hda

---

### Post by j0rg3 on 2011-09-05
It does show 

```
% aplay -l
aplay: device_list:240: no soundcards found...

% aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
```

Huh!  I didn't notice this before but I get *entirely* different answers as 'root'.


```
# aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct sample mixin# aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakersg device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```

```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Not entirely sure what to do with that information but back to Google I go!  (:

---

### Post by BicyclerBoy on 2011-09-05
You could check your user is a member of the audio group.

You should not need to use sudo aplay..

Have you re-installed alsa from outside the package management system ?

---

### Post by j0rg3 on 2011-09-06
Yup; you nailed it!  I added my user to the 'audio' group and, after a reboot, I now have sound.

Thanks for the help!

---


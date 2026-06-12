---
title: "Distorted sound after a while using mic"
date: 2011-06-09
forum: Multimedia Software
---

### Post by logiq on 2011-06-09
I run two sound cards on my system, one dedicated while the other is built-in on my motherbard. 

```
cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdfff0000 irq 23
 1 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown
```

```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

```
Linux version 2.6.38-10-generic-pae (buildd@roseapple) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #44-Ubuntu SMP Thu Jun 2 21:50:56 UTC 2011
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I am not able to get any sound recorded through my mic using my XFi card. It records the sound my computer makes, thought. In other words, if I play a song, it'll play through the capture channel making people on voip application hear it. For some reason. But I am not able to get any sound through the mic.

I have tried to mute and unmute every channel in alsamixer, and tried to change the soundcard profile as well in gnome sound preferences. No luck.

If I use my NVidia built-in sound card however, I am able to talk. But after a random period of time, the sound through my headphones begin to distort, badly, while the voice from my mic comes through clear. People can hear me clearly, but I can't hear them at all because of the distortion. It sound really, really bad.

At first I thought it was a bug with skype, but it happens in other voip clients such as gTalk.

Any assistance would be greatly appreciated,

Thanks in advance.

---

### Post by lidex on 2011-06-09
What about arecord output:
```
arecord -L
```

---

### Post by logiq on 2011-06-10
This is a long one:

```
arecord -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Front speakers
surround40:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.0 Surround output to Front and Rear speakers
surround41:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Direct sample mixing device
dsnoop:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Direct sample snooping device
hw:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Direct hardware device without any conversions
plughw:CARD=XFi,DEV=0
    Creative X-Fi, Front/WaveIn
    Hardware device with all software conversions
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
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=2
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=2
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=2
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=2
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, ALC1200 Digital
    Hardware device with all software conversions
```

---

### Post by lidex on 2011-06-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by logiq on 2011-06-12
[http://www.alsa-project.org/db/?f=f11ba0dac3ee8a74c2e0d1a718ff3e7bfbddd328](http://www.alsa-project.org/db/?f=f11ba0dac3ee8a74c2e0d1a718ff3e7bfbddd328)

---

### Post by lidex on 2011-06-13
Where are you plugging in the mic for the X-fi? Line or mic?

---

### Post by logiq on 2011-06-14
Mic.

---

### Post by lidex on 2011-06-15
Try muting the capture portion of these elements:
```
Simple mixer control 'Master',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 158 [62%] [-24.50dB] Capture 256 [100%] [0.00dB]
  Front Right: Playback 158 [62%] [-24.50dB] Capture 256 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 256 Capture 0 - 256
  Front Left: Playback 256 [100%] [0.00dB] Capture 234 [91%] [-5.50dB] [on]
  Front Right: Playback 256 [100%] [0.00dB] Capture 234 [91%] [-5.50dB] [on]
```

---


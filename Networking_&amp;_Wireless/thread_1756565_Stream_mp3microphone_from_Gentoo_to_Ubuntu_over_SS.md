---
title: "Stream mp3/microphone from Gentoo to Ubuntu over SSH"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by TeaGoblin on 2011-05-12
Hey

I would like to play music and be able to hear the microphone from my local machine on a remote machine (bob@home) with a ssh server running.

I googled around but only found references to /dev/dsp which does not exist in ubuntu 11.04. Below is a list of the existing devices.

I use this for getting it done but it's ugly and cumbersome:
dd if=song.mp3 | ssh bob dd of=/tmp/song.mp3 && ssh bob mplayer /tmp/song.mp3 

What is The Right Way to stream music (mp3/ogg) or microphone output from my Gentoo machine (ALSA) to Ubuntu 11.04 (Pulse)?

```
bob@home:~$ ll /dev/dsp
ls: cannot access /dev/dsp: No such file or directory
bob@home:~$ find /dev/snd/
/dev/snd/
/dev/snd/by-path
/dev/snd/by-path/pci-0000:00:1b.0
/dev/snd/controlC0
/dev/snd/hwC0D0
/dev/snd/hwC0D1
/dev/snd/pcmC0D0c
/dev/snd/pcmC0D0p
/dev/snd/pcmC0D1p
/dev/snd/pcmC0D2c
/dev/snd/seq
/dev/snd/timer
bob@home:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bob@home:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC268 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Hardware device with all software conversions
```

---


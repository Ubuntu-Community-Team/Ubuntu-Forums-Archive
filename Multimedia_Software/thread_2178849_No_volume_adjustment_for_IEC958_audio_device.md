---
title: "No volume adjustment for IEC958 audio device"
date: 2013-10-05
forum: Multimedia Software
---

### Post by Fincer on 2013-10-05
Hey,

I recently updated my computer hardware with [Asus M5A99X EVO R2.0 motherboard]("http://www.asus.com/Motherboards/M5A99X_EVO_R20/"). This motherboard comes with integrated audio

```
lspci
...
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
...
```

My audio goes through rear SDPIF output (optical audio).

```
aplay -L

sysdefault:CARD=SB
    HDA ATI SB, ALC892 Analog
    Default Audio Device
front:CARD=SB,DEV=0                                                                                                                                
    HDA ATI SB, ALC892 Analog                                                                                                                      
    Front speakers                                                                                                                                 
surround40:CARD=SB,DEV=0                                                                                                                           
    HDA ATI SB, ALC892 Analog                                                                                                                      
    4.0 Surround output to Front and Rear speakers                                                                                                 
surround41:CARD=SB,DEV=0                                                                                                                           
    HDA ATI SB, ALC892 Analog                                                                                                                      
    4.1 Surround output to Front, Rear and Subwoofer speakers                                                                                      
surround50:CARD=SB,DEV=0                                                                                                                           
    HDA ATI SB, ALC892 Analog                                                                                                                      
    5.0 Surround output to Front, Center and Rear speakers                                                                                         
surround51:CARD=SB,DEV=0                                                                                                                           
    HDA ATI SB, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, ID aa01 Digital
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, ID aa01 Digital
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, ID aa01 Digital
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, ID aa01 Digital
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, ID aa01 Digital
    Hardware device with all software conversions
```

My *.asoundrc* reads as follow:

```
pcm.!default iec958:SB
```

Well, I encountered a nasty problem. The audio plays fine but I'm not able to adjust ANY audio volume levels. My OS is Kubuntu 13.10 64-bit with following package versions
kernel: 3.11.0-11-generic (tried another version as well)
alsa-base: 1.0.25+dfsg-0ubuntu4
alsa-utils: 1.0.27.1-1ubuntu1

I'm not using Pulseaudio frontend, audio plays straight through ALSA. My current Phonon backend is VLC 0.6.2 (alternatively GStreamer 4.6.3).

I've already tried to switch the kernel without breakthrough. I have no idea why I don't have any volume level adjustment controls in Kmix for IEC958 channel. The channel works just like ON/OFF switch - no adjustments of any kind. Very frustating and I have no idea about a possible solution.

Here's couple of screenshots.

Kmix - there is no volume level adjustments for IEC958 channel:

[IMG]http://88.192.69.68/ftp/public/other/kmix_no_adjustments.jpg[/IMG]

Alsamixer - no IEC958 channel visible at all:

[IMG]http://88.192.69.68/ftp/public/other/alsamixer_no_adjustments.jpg[/IMG]

IEC958 is currently the only channel I'm even able to get some audio playback. All other channels are "muted" (i.e. no sound).

Any help is VERY appreciated.

- Fincer

---

### Post by Yellow Pasque on 2013-10-05
Try stopping kmix and restarting with this command:
```
export KMIX_PULSEAUDIO_DISABLE=1; kmix&
```
Any better?

---


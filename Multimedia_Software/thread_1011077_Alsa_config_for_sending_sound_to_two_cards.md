---
title: "Alsa config for sending sound to two cards"
date: 2008-12-14
forum: Multimedia Software
---

### Post by sserdyuk on 2008-12-14
Hi,

I've searched for an example and there are many out there but I could not piece one I need.

I have a HTPC with three sound cards 
[LIST=1]
[*]SB: On board connected to headphone sockets on the back of the computer
[*]HDMI: On board connected to HDMI output
[*]CMI8738: PCI add-on
[/LIST]

My goal is to have playback for stereo, AC3 and DTS audio without switching things around.

The first card (SB) is pretty useless, so I do not use it.

HDMI goes out to the TV, which does not have AC3 decoder, so audio has to be downmixed to stereo.

PCI add-on (CMI8738 ) goes to the receiver via optical cable, so audio has be in the original format, all decoding left to the receiver.

I'd like to have a default card that everything plays sound to and then it gets sent to HDMI and PCI-spdif all the time, so I can simply turn the receiver on if I want rich sound.

Can someone help please?

Some information about my system:

Intrepid 64bit
Kernel 2-6-27-9

```
$ asoundconf list
Names of available sound cards:
CMI8738
SB
HDMI

$ aplay -L
default:CARD=CMI8738
    C-Media CMI8738, C-Media PCI DAC/ADC
    Default Audio Device
front:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Front speakers
iec958:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, ALC883 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC883 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
front:CARD=HDMI
    HDA ATI HDMI
    Front speakers
surround40:CARD=HDMI
    HDA ATI HDMI
    4.0 Surround output to Front and Rear speakers
surround41:CARD=HDMI
    HDA ATI HDMI
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=HDMI
    HDA ATI HDMI
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=HDMI
    HDA ATI HDMI
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers

```

---

### Post by markbuntu on 2008-12-14
You can do this with pulseaudio but you must make devices for the digital output first.

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

Then you can make a virtual device that combines them

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---


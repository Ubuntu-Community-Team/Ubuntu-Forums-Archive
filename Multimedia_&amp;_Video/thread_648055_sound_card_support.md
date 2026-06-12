---
title: "sound card support"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by gupta_sumesh63 on 2007-12-23
Hi,
It may be a silly question, but can anyone tell me how to determine if my soundcard supports 5.1 sorround or 7.1 or 6channels or 4 cahnnels. I have 3 sockets at the rear of the box. line-in, line out and mic.
Secondly , how do I configure Alsa to run 5.1 or 7.1 etc.
Thanks in advance

---

### Post by adelodder on 2007-12-23
What output do you get when you type "aplay -L" without brackets in Terminal?

This is my output:

```
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device
default:CARD=Headset
    BT Headset, BT SCO PCM
    Default Audio Device

```

---

### Post by gupta_sumesh63 on 2007-12-23
Hi,
This is the output of "aplay -L"

> sumesh@lt-d80695157124:~$ aplay -L
default:CARD=Intel
    HDA Intel, ALC880 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC880 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

---

### Post by gupta_sumesh63 on 2007-12-23
> **adelodder said:**
> What output do you get when you type "aplay -L" without brackets in Terminal?

This is my output:

```
default:CARD=CK804
    NVidia CK804, NVidia CK804
    Default Audio Device
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=UART
    MPU-401 UART
    Default Audio Device
default:CARD=Headset
    BT Headset, BT SCO PCM
    Default Audio Device

```

What does this imply??

---

### Post by gupta_sumesh63 on 2007-12-24
Anyone with some help please?

---


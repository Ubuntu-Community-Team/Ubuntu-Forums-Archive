---
title: "How to clone the sound signal to the blue jack?"
date: 2008-09-12
forum: Multimedia Software
---

### Post by cherva on 2008-09-12
Is there a way to clone the sound from the green jack to the blue one ? I am using OSS v4 with a High Definition Audio ALC861 sound card. Well there must be a way because it's linux :) , but can someone tell me how to do it ? I ossxmix for the blue jack I have the options: rearmix and input. Here are my current settings in ossxmix. ossinfo: 
```
Version info: OSS 4.0 (b1016/200807241529) (0x00040003) 
Platform: Linux/i686 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 (mitosoft)

Number of audio devices:	6
Number of audio engines:	10
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 VIA HD Audio interrupts=7988444 (9009195)
    HD Audio controller VIA HD Audio
    Vendor ID    0x11063288
    Subvendor ID 0x104381e7
     Codec  0: ALC861 (0x10ec0861/0x1043c601)
 2: ossusb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC861 (Mixer 0 of device object 1)

Audio devices
HD Audio play front               /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio play side                /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio play center/LFE          /dev/oss/hdaudio0/pcm2  (device index 2)
HD Audio play rear                /dev/oss/hdaudio0/pcm3  (device index 3)
HD Audio play spdout              /dev/oss/hdaudio0/spdout0  (device index 4)
HD Audio rec rec                  /dev/oss/hdaudio0/pcmin0  (device index 5)

```

---

### Post by cherva on 2008-09-13
I guess no one knows how to do this....

---


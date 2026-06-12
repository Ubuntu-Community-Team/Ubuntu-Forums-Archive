---
title: "HDMI audio not working"
date: 2010-02-03
forum: Multimedia Software
---

### Post by nimbus00 on 2010-02-03
I have a Mythbuntu 9.0.4 fresh install and seem to be having issues with audio over HDMI. I can get audio over the headset output (green round port). 

I am guessing this probably has something to do with the default sound card that is used to output when I play something, say internet radio. But I can't figure out how to configure Ubuntu to use the HDMI output as default. Any help is appreciated. 

The motherboard is: 
[http://www.legitreviews.com/article/691/1/](http://www.legitreviews.com/article/691/1/)

Output of the following:
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9e8000 irq 19

Output of the following: 
$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

Output of the following: 
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Output of the following:
$ aplay -L
default:CARD=SB
    HDA ATI SB, STAC92xx Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

Thanks, 
Nimbus

---


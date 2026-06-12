---
title: "No sound from rear speaker, but front works"
date: 2011-02-03
forum: Multimedia Software
---

### Post by rcuswalk on 2011-02-03
I recently bought an HP Pavilion Elite HPE-570t. Except for the fact that I can't get the back speaker jack to work, Maverick works great. Here's info that seems relevant:


aplay -l

card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

++++++++

aplay -L

default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, ATI HDMI
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Hardware device with all software conversions

++++++++

lspci

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

++++++++

cat /proc/asound/cards

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfe700000 irq 51
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe640000 irq 53

++++++++

cat /proc/asound/modules

 0 snd_hda_intel
 1 snd_hda_intel

++++++++

I've look at Alsa Mixer. There are two tabs (IDT ID 76c7 and ATI R6xx HDMI). I turned the second one off, since I don't have any HDMI sound output device connected to the computer. On the other tab, there are five sliders (Master, PCM, Front Mi, Line and Mic). They are all turned on, and the first two are at maximum volume.

It seems to me that Ubuntu is not recognizing whatever controls the rear speaker jack.

Can anyone steer me in the right direction to get this fixed? Thanks.

---

### Post by reto on 2011-03-30
I'm having the same problem. Also I didn't get the microhpne working, does this work for you?

Cheers,
reto

---


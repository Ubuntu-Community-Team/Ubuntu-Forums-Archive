---
title: "HDMI sound in myth OK outside"
date: 2010-07-05
forum: Mythbuntu
---

### Post by axelsvag on 2010-07-05
I have problem getting the HDMI sound working in Mythtv though it is working perfectly outside Mythtv for example vlc, SMplayer, Totem etc.
I got the GT 240 nvidia card 256 driver and alsa 1.0.23. The system is hooked up with a HDMI. The version of Mythbuntu is 32 bit Mythbuntu 10.04. Maybe it is so easy as changing the sound device to something different in the Mythfrontend sound settings menu but to what. ??

---

### Post by Neon Dusk on 2010-07-05
What does aplay -l return?

What do you have set in mythtv -> setup -> general -> [Audio System Page]?

---

### Post by axelsvag on 2010-07-05
aplay -l returns the nvidia hdmi card as device 1,3. But if I use ALSA:hw:1,3 in myth frontend nothing gets better. I will look better tomorrow what it says

---

### Post by Neon Dusk on 2010-07-05
It would be useful to see if anything shows up in the frontend log or try starting using mythfrontend -v playack,audio

I use ALSA:hdmi:1 in mythfrontend for a G210 card.

---

### Post by nickrout on 2010-07-05
> **axelsvag said:**
> aplay -l returns the nvidia hdmi card as device 1,3. But if I use ALSA:hw:1,3 in myth frontend nothing gets better. I will look better tomorrow what it says

You shouldn't need that, ALSA:hdmi should work.

Another poster suggests ASA:hdmi:1 , which I assume means he had two hdmi devices and :1 is the second one.

Anyway if you still can't get it working please post the output of aplay -l and aplay -L

---

### Post by trevs.bronco on 2010-07-05
I am having the same issue, only mine started after the last update. I have a geforce 210 card and Alsa 1.0.23. I believe it was working with the ALSA:plughw:0,7, but now my card is 1,7 as the onboard audio is being detected. I believe I have tried every setting, but nothing has worked, is there something else or some where else we should be looking?
Thanks,

Trev

---

### Post by nickrout on 2010-07-05
> **trevs.bronco said:**
> I am having the same issue, only mine started after the last update. I have a geforce 210 card and Alsa 1.0.23. I believe it was working with the ALSA:plughw:0,7, but now my card is 1,7 as the onboard audio is being detected. I believe I have tried every setting, but nothing has worked, is there something else or some where else we should be looking?
Thanks,

Trev

output of aplay -l and aplay -L ???

---

### Post by trevs.bronco on 2010-07-05
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1708S Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
```

Trev

---

### Post by nickrout on 2010-07-05
Trev, try simply ALSA:hdmi as your output device in mythtv frontend (Setup, General I think)

---

### Post by trevs.bronco on 2010-07-05
> **nickrout said:**
> Trev, try simply ALSA:hdmi as your output device in mythtv frontend (Setup, General I think)
tried that and ALSA:hdmi:1, neither work. Any other suggestions?

Trev

---

### Post by trevs.bronco on 2010-07-05
Doh! took a look at the frontend log, which was corrupt when i tried to view it when this problem started. and low and behold the sound card was in use so no audio. closed everything that was open, and voila sound!

The setting I am using is ALSA:default

Trev

---

### Post by nickrout on 2010-07-06
Ahh problem solved by looking in logs, how novel!

---


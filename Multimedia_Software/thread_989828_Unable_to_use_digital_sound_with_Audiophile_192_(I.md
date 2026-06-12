---
title: "Unable to use digital sound with Audiophile 192 (ICE958)"
date: 2008-11-22
forum: Multimedia Software
---

### Post by das letzte einhorn on 2008-11-22
I wish to use my Sennheiser RS136 headphones with my Audiophile 192 with the S/PDIF output instead of analog. These headphones have jacks which do fit into S/PDIF plugs, hence I assume they are compatible with that mode.

What I don't understand is that despite not being mute (alsamixer), no sound at all can be heard when I attempt to use digital. I also had a look at the comprehensive guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), without success. Here is the output of aplay -l and aplay -L.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audiophile192 [M Audio Audiophile192], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audiophile192 [M Audio Audiophile192], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
xavier@xavier:~$ aplay -L
front:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    Front speakers
rear:CARD=Audiophile192,DEV=0
    M Audio Audiophile192
    Rear speakers
center_lfe:CARD=Audiophile192,DEV=0
    M Audio Audiophile192
    Center and Subwoofer speakers
side:CARD=Audiophile192,DEV=0
    M Audio Audiophile192
    Side speakers
surround40:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
[B]iec958:CARD=Audiophile192,DEV=0
    M Audio Audiophile192, ICE1724
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)[/B]

I have highlighted a part which seems curious to me. Anyone has a suggestion on how to make it work? Is it possible that despite having fitting jacks, that these headphones are not compatible with digital output? Thanks for your help.

---


---
title: "no sound from my rear speakers"
date: 2013-05-27
forum: Multimedia Software
---

### Post by sionut on 2013-05-27
Hi,
I have a Xonar DX sound card installed on a xbmcbuntu system:

```
$ uname -a
Linux our-xbmc 3.0.0-28-generic-pae #45-Ubuntu SMP Wed Nov 14 21:58:38 UTC 2012 i686 i686 i386 GNU/Linux
```

The sound card is configured and it shows just fine as:

```
$cat /proc/asound/cards 
 0 [DX             ]: AV200 - Xonar DX
                      Asus Virtuoso 100 at 0xe000, irq 16
```

All the channels are unmuted in alsamixer (Master front, Master rear, Master center, Master woofer, Master side).

Here's the output of aplay -L:

```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=DX
    Xonar DX, Multichannel
    Default Audio Device
front:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Front speakers
surround40:CARD=DX,DEV=0
    Xonar DX, Multichannel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=DX,DEV=0
    Xonar DX, Multichannel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=DX,DEV=0
    Xonar DX, Multichannel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=DX,DEV=0
    Xonar DX, Multichannel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=DX,DEV=0
    Xonar DX, Multichannel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=DX,DEV=0
    Xonar DX, Multichannel
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Direct sample mixing device
dmix:CARD=DX,DEV=1
    Xonar DX, Digital
    Direct sample mixing device
dsnoop:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Direct sample snooping device
dsnoop:CARD=DX,DEV=1
    Xonar DX, Digital
    Direct sample snooping device
hw:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Direct hardware device without any conversions
hw:CARD=DX,DEV=1
    Xonar DX, Digital
    Direct hardware device without any conversions
plughw:CARD=DX,DEV=0
    Xonar DX, Multichannel
    Hardware device with all software conversions
plughw:CARD=DX,DEV=1
    Xonar DX, Digital
    Hardware device with all software conversions
```

However, when I run the following test, I can hear noise only from front speakers, center and the subwoofer and nothing from the rear speakers:
```
speaker-test -Dsurround51:DX -c6
```

Just to be sure that there is no connectivity problem for the rear speakers, I made a simple test: I inserted the rear jack into the front output and I can confirm that the rear speakers are just fine. 

I would really appreciate any advice (I've been trying to configure the card for 5 days now and it's really getting on my nerves)

---

### Post by sionut on 2013-05-29
I solved it. It was simply a problem of inserting the rear speakers jack in the output marked as "side" instead of "back". 

I guess this is true only for a 6 channel configuration (I have a 5.1 X530 Logitech).

---


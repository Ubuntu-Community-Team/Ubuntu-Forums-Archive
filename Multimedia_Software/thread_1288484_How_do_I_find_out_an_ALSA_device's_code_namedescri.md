---
title: "How do I find out an ALSA device's code name/description thing?"
date: 2009-10-11
forum: Multimedia Software
---

### Post by Endolith on 2009-10-11
I've searched over and over and can't find any explanation of what "hw:0,0" means.  How do I determine the number of my USB audio card?  If I do "alsamixer -c 1" it opens the USB card's volume control, but that really doesn't help me.  Where are the device names/numbers listed or explained?

```
> aplay -L
default:CARD=I82801DBICH4
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Default Audio Device
front:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    Front speakers
surround40:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.0 Surround output to Front and Rear speakers
surround41:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=I82801DBICH4,DEV=0
    Intel 82801DB-ICH4, Intel 82801DB-ICH4 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=default
    USB Audio CODEC , USB Audio
    Default Audio Device
front:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by markbuntu on 2009-10-11
cat /proc/asound/cards

---


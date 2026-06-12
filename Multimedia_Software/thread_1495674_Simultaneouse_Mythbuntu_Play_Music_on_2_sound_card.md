---
title: "Simultaneouse Mythbuntu Play Music on 2 sound cards"
date: 2010-05-28
forum: Multimedia Software
---

### Post by ale99 on 2010-05-28
Dear Forum,
I am looking for suggestions for how can I play Mythtv audio (Play Music) on two sound cards simultaneously. 
I have two cards working well. One card is an onboard Intel cards, and the other card is a USB Audio card. Both cards are working well. I use the onboard Intel to output SPDIF to an amplified. The second USB card is bound to MPD service and it outputs an analog signal to a second amplified. 

I'd like to cancel my MPD and have the following configuration:

Mythtv play to the default card with 5.1 passthrough, while the second card, connected to a second amplifier, plays an analog signal to the same audio played by Mythtv Play Music. 

In other words, I need to mix somehow the two cards. 
Here is the list of cards: 
root@mythtv:~# aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC660-VD Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC660-VD Digital
    IEC958 (S/PDIF) Digital Audio Output
default:CARD=default
    USB Sound Device        , USB Audio
    Default Audio Device
front:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    USB Sound Device        , USB Audio
    IEC958 (S/PDIF) Digital Audio Output
Any ideas? 

Thanks,

Ale99

---


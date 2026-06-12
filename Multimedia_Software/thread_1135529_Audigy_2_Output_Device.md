---
title: "Audigy 2 Output Device"
date: 2009-04-24
forum: Multimedia Software
---

### Post by BigErn on 2009-04-24
Hi, I'm having a problem that's driving me nuts.  I have an Audigy 2 Value sound card and in KDE (4.2) All of the sound output device options resulted in muffled, almost inaudible sound, except for "ADC Capture/Standard PCM Playback IEC958 (S/PDIF) Digital Audio Output".  That by itself is strange because I don't think I'm using SPDIF...

 but anyway- so I can't choose this output device in the Gnome "Sound Preferences" Dialog, as it's not in the drop down list.  In KDE I had to check the show advanced devices options to get the SPDIF option to even show up, but in Gnome there's no such checkbox.  Is there a way to get Gnome to be able to use the right output device?  Or better yet not have to use that output device and be able to use the normal one?  The sound configuration in Ubuntu is very confusing..

Here's the output of aplay -L

default:CARD=Audigy2
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    Audigy 2 Value [SB0400], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

---

### Post by BigErn on 2009-04-24
Nevermind, I was using the wrong plugs of my 5.1 speakers- hence the muffled sound!

---


---
title: "envy24control - alsa device names"
date: 2011-11-14
forum: Multimedia Software
---

### Post by Kevin Golding on 2011-11-14
I've got a Delta 1010LT multichannel sound card which I can see working (capturing audio input) in envy24control, but I can not get it to work using sox on the command line.

I think I'm missing the device name to use that corresponds to the envy24control's "H/W In 3" (etc) channels.

alsamixer and envy24control show all channels unmuted and the gain's turned up.

# arecord -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=M1010LT
    M Audio Delta 1010LT, ICE1712 multi
    Default Audio Device
front:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    Front speakers
surround40:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M1010LT,DEV=0
    M Audio Delta 1010LT, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output

---


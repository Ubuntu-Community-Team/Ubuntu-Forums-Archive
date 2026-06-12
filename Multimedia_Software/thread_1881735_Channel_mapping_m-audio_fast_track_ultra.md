---
title: "Channel mapping m-audio fast track ultra"
date: 2011-11-16
forum: Multimedia Software
---

### Post by abocanegra on 2011-11-16
So I have managed to get my m-audio fast track ultra to be seen and to send tones out of the outputs. 

However, I am still having difficulty mapping the channels correctly in the .asoundrc file. Any help will be greatly appreciated. 

Here are my issues:
My card reads as a 7.1 and jack fails to connect when set to the actual 6 channels it has. (card has 6 analog out and 2 digital). 
Audio outputs in both Supercollider and using speaker-test. However when I do multichannel it seems to only output from channel 1.

I have the latest alsa compiled.

**aplay -l**
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Ultra [Fast Track Ultra], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
[B]
aplay -L[/B]
```

null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC663 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC663 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC663 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
default:CARD=Ultra
    Fast Track Ultra, USB Audio
    Default Audio Device
front:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    Front speakers
surround40:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Ultra,DEV=0
    Fast Track Ultra, USB Audio
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by abocanegra on 2011-11-16
Figured it out. I had it working all along, but I hadn't gone to alsamixer in command line and muted the correct channels. Each channel had all 8 active and I had to make sure each channel only had it's own channel unmuted.

---


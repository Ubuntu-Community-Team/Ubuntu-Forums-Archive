---
title: "CMI 8770 card not working upon system upgrade"
date: 2009-12-19
forum: Multimedia Software
---

### Post by dpj on 2009-12-19
I recently upgraded a Kubuntu/Ubuntu system to 9.10 / kernel 2.6.31-16 from one previously running on kernel 2.6.28-13 (8.10 I think) and when I did so its CMI 8770-based PCI sound card ceased to work. The system also has an onboard sound card which continues to work.

The snd_cmipci module is being loaded.

The output of aplay -l is:

```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8770 [C-Media CMI8770], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8770 [C-Media CMI8770], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8770 [C-Media CMI8770], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```and aplay -L (for PCM device names):
```

front:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    Front speakers
surround40:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.0 Surround output to Front and Rear speakers
surround41:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=V8237,DEV=0
    VIA 8237, VIA 8237
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI DAC/ADC
    Front speakers
surround40:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=CMI8770,DEV=0
    C-Media CMI8770, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output

```I tested the sound on the C-Media front device:

```

aplay -D front:CARD=CMI8770,DEV=0 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:608: audio open error: Device or resource busy

```
This is a bit of annoying puzzle since all is apparently well except it claims to be busy when trying to use it.

---


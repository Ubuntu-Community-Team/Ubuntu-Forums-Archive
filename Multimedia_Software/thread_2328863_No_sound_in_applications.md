---
title: "No sound in applications"
date: 2016-06-25
forum: Multimedia Software
---

### Post by jens19 on 2016-06-25
Recently the sound on my laptop stopped working in applications, however when I test the speaker sound in system settings or through speaker-test the sound still comes through. This applies both to when I have headphones plugged in and when I try to use the default speakers. I am currently stumped.

This is the alsa info-script output: [http://www.alsa-project.org/db/?f=537420486d74515c711078f4f426368883cb301d](http://www.alsa-project.org/db/?f=537420486d74515c711078f4f426368883cb301d)

aplay -l && aplay -L gives this output:
```
**** List of PLAYBACK Hardware Devices ****card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: 92HD91BXX Analog [92HD91BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=HDMI,DEV=0
    HDA Intel HDMI, HDMI 0
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=1
    HDA Intel HDMI, HDMI 1
    HDMI Audio Output
hdmi:CARD=HDMI,DEV=2
    HDA Intel HDMI, HDMI 2
    HDMI Audio Output
sysdefault:CARD=PCH
    HDA Intel PCH, 92HD91BXX Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD91BXX Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD91BXX Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD91BXX Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD91BXX Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD91BXX Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, 92HD91BXX Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

```

---

### Post by jens19 on 2016-06-25
update: when plugging in my laptop to the TV through hdmi I was able to get sound from the TV, however still no sound normally from my computer.

---

### Post by Yellow Pasque on 2016-06-26
Try resetting pulse configuration.
```
rm -r ~/.conf/pulse*
pulseaudio -k
```

---

### Post by jens19 on 2016-07-21
> **Temüjin said:**
> Try resetting pulse configuration.
```
rm -r ~/.conf/pulse*
pulseaudio -k
```
Thank you, this appears to have solved my issues.

---


---
title: "ATI HDMI sound problem (ALSA)"
date: 2010-02-28
forum: Multimedia Software
---

### Post by Glaucous on 2010-02-28
Hello. I've been fixing around with sound on Ubuntu today, so far I got most of it working. I'm still not able to get sound through ATI 4870 HDMI (it works on Windows 7), it worked on pulseaudio, but I wanted to change to ALSA.

aplay -L
```
default:CARD=SB
    HDA ATI SB, ALC888 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Headset
    Logitech USB Headset, USB Audio
    Default Audio Device
front:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
default:CARD=Live
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
surround40:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Live,DEV=0
    SB Live! Value [SB0101], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=Live,DEV=0
    SB Live! Value [SB0101], Multichannel Capture/PT Playback
    IEC958 (S/PDIF) Digital Audio Output
```

Card=SB (0) is my integrated soundcard, Realtek, I use this for SPDIF coaxial to be able to use my AVR without having to use HDMI - this is only for music.

Card=HEADSET (1) is my USB headset, probably no problems there.

Card=Live (2) is my PCI creative SB Live 5.1 card, using this for my PC speakers, actually gave me a nice FPS boost in games compared to my integrated.

All those soundcards works perfect, but as you can see, ATI HDMI isn't listed.

aplay -l
I striped this code a bit, obviously the cards which worked above is also listed here.
```
card 3: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Here is ATI HDMI, but it is not working, not with speaker-test nor mplayer (obvious, I guess..). I read the sticky regarding soundcards and I'm looking for a modprobe for HDMI, which I can't find.

I have Gnome ALSA Mixer as well, which lists REALTEK ALC888, USB Mixer, Sigmatel and lastly ATI R6xx HDMI - the ATI one does not have sliders.

---

### Post by jweaver28 on 2010-03-02
Me too. And my postings on other threads haven't been answered. But hope springs eternal!

---

### Post by rick_ca on 2010-12-10
Did either of you ever solve this problem?

I'm having the same problem using Ubuntu 10.10 and an ATI Radeon Xpress 1200 Series (RS600).

---


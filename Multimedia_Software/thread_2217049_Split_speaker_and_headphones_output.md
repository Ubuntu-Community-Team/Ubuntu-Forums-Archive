---
title: "Split speaker and headphones output"
date: 2014-04-15
forum: Multimedia Software
---

### Post by henk6 on 2014-04-15
Hello,

I want to split the headphones (3.5mm jack) and internal speakers of a laptop to 2 different audio outputs. I've read some things on the internet and create a virtual sound device in ".asoundrc" but it doesn't work. So could someone help me with this?

Ouput of aplay -L:
```

[FONT=arial]ubuntu@lubuntu:~$ aplay -L[/FONT]
[FONT=arial]null[/FONT]
[FONT=arial]    Discard all samples (playback) or generate zero samples (capture)[/FONT]
[FONT=arial]pulse[/FONT]
[FONT=arial]    PulseAudio Sound Server[/FONT]
[FONT=arial]default[/FONT]
[FONT=arial]    Playback/recording through the PulseAudio sound server[/FONT]
[FONT=arial]sysdefault:CARD=PCH[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    Default Audio Device[/FONT]
[FONT=arial]front:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    Front speakers[/FONT]
[FONT=arial]surround40:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    4.0 Surround output to Front and Rear speakers[/FONT]
[FONT=arial]surround41:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    4.1 Surround output to Front, Rear and Subwoofer speakers[/FONT]
[FONT=arial]surround50:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    5.0 Surround output to Front, Center and Rear speakers[/FONT]
[FONT=arial]surround51:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    5.1 Surround output to Front, Center, Rear and Subwoofer speakers[/FONT]
[FONT=arial]surround71:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers[/FONT]
[FONT=arial]hdmi:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, HDMI 0[/FONT]
[FONT=arial]    HDMI Audio Output[/FONT]
[FONT=arial]dmix:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    Direct sample mixing device[/FONT]
[FONT=arial]dmix:CARD=PCH,DEV=3[/FONT]
[FONT=arial]    HDA Intel PCH, HDMI 0[/FONT]
[FONT=arial]    Direct sample mixing device[/FONT]
[FONT=arial]dsnoop:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    Direct sample snooping device[/FONT]
[FONT=arial]dsnoop:CARD=PCH,DEV=3[/FONT]
[FONT=arial]    HDA Intel PCH, HDMI 0[/FONT]
[FONT=arial]    Direct sample snooping device[/FONT]
[FONT=arial]hw:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    Direct hardware device without any conversions[/FONT]
[FONT=arial]hw:CARD=PCH,DEV=3[/FONT]
[FONT=arial]    HDA Intel PCH, HDMI 0[/FONT]
[FONT=arial]    Direct hardware device without any conversions[/FONT]
[FONT=arial]plughw:CARD=PCH,DEV=0[/FONT]
[FONT=arial]    HDA Intel PCH, STAC92xx Analog[/FONT]
[FONT=arial]    Hardware device with all software conversions[/FONT]
[FONT=arial]plughw:CARD=PCH,DEV=3[/FONT]
[FONT=arial]    HDA Intel PCH, HDMI 0[/FONT]
[FONT=arial]    Hardware device with all software conversions[/FONT]

```

Greets,

Janco

---


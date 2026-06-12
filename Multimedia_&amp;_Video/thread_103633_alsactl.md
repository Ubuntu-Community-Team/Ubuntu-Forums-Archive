---
title: "alsactl"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by Jabone on 2005-12-14
I get warnings from alsactl when booting my computer. I recently upgraded my kernel to 2.6.14 and some settings in my mixer disappeared (emu10k1 pcmX). I have breezy alsa-base and alsa-utils etc. packages installed. 

Basic controls are available others not. How can I test which output is which and make a working asound.state file?

Thanks for your help

Jabone

cat /proc/asound/card0/emu10k1
EMU10K1

Card                  : Creative
Internal TRAM (words) : 0x2000
External TRAM (words) : 0x8000

Effect Send Routing   :
Ch0: A=0, B=1, C=2, D=3
Ch1: A=0, B=1, C=2, D=3
Ch2: A=0, B=1, C=2, D=3
Ch3: A=0, B=1, C=2, D=3
Ch4: A=0, B=1, C=2, D=3
Ch5: A=0, B=1, C=2, D=3
Ch6: A=0, B=1, C=2, D=3
Ch7: A=0, B=1, C=2, D=3
Ch8: A=0, B=1, C=2, D=3
Ch9: A=0, B=1, C=2, D=3
Ch10: A=0, B=1, C=2, D=3
Ch11: A=0, B=1, C=2, D=3
Ch12: A=0, B=1, C=2, D=3
Ch13: A=0, B=1, C=2, D=3
Ch14: A=0, B=1, C=2, D=3
Ch15: A=0, B=1, C=2, D=3
Ch16: A=0, B=1, C=2, D=3
Ch17: A=0, B=1, C=2, D=3
Ch18: A=0, B=1, C=2, D=3
Ch19: A=0, B=1, C=2, D=3
Ch20: A=0, B=1, C=2, D=3
Ch21: A=0, B=1, C=2, D=3
Ch22: A=0, B=1, C=2, D=3
Ch23: A=0, B=1, C=2, D=3
Ch24: A=0, B=1, C=2, D=3
Ch25: A=0, B=1, C=2, D=3
Ch26: A=0, B=1, C=2, D=3
Ch27: A=0, B=1, C=2, D=3
Ch28: A=0, B=1, C=2, D=3
Ch29: A=0, B=1, C=2, D=3
Ch30: A=0, B=1, C=2, D=3
Ch31: A=0, B=1, C=2, D=3
Ch32: A=0, B=1, C=2, D=3
Ch33: A=0, B=1, C=2, D=3
Ch34: A=0, B=1, C=2, D=3
Ch35: A=0, B=1, C=2, D=3
Ch36: A=0, B=1, C=2, D=3
Ch37: A=0, B=1, C=2, D=3
Ch38: A=0, B=1, C=2, D=3
Ch39: A=0, B=1, C=2, D=3
Ch40: A=0, B=1, C=2, D=3
Ch41: A=0, B=1, C=2, D=3
Ch42: A=0, B=1, C=2, D=3
Ch43: A=0, B=1, C=2, D=3
Ch44: A=0, B=1, C=2, D=3
Ch45: A=0, B=1, C=2, D=3
Ch46: A=0, B=1, C=2, D=3
Ch47: A=0, B=1, C=2, D=3
Ch48: A=0, B=1, C=2, D=3
Ch49: A=0, B=1, C=2, D=3
Ch50: A=0, B=1, C=2, D=3
Ch51: A=0, B=1, C=2, D=3
Ch52: A=0, B=1, C=2, D=3
Ch53: A=0, B=1, C=2, D=3
Ch54: A=0, B=1, C=2, D=3
Ch55: A=0, B=1, C=2, D=3
Ch56: A=0, B=1, C=2, D=3
Ch57: A=0, B=1, C=2, D=3
Ch58: A=0, B=1, C=2, D=3
Ch59: A=0, B=1, C=2, D=3
Ch60: A=0, B=1, C=2, D=3
Ch61: A=0, B=1, C=2, D=3
Ch62: A=0, B=1, C=2, D=3
Ch63: A=0, B=1, C=2, D=3

Captured FX Outputs   :
  Output 16 [???]
  Output 17 [Analog Center]
  Output 18 [Analog LFE]
  Output 19 [???]
  Output 20 [???]
  Output 21 [???]
  Output 22 [???]
  Output 23 [???]
  Output 24 [???]
  Output 25 [???]
  Output 26 [???]
  Output 27 [???]
  Output 28 [???]
  Output 29 [???]
  Output 30 [???]
  Output 31 [???]

All FX Outputs        :
  Output 00 [AC97 Left]
  Output 01 [AC97 Right]
  Output 02 [Optical IEC958 Left]
  Output 03 [Optical IEC958 Right]
  Output 04 [Center]
  Output 05 [LFE]
  Output 06 [Headphone Left]
  Output 07 [Headphone Right]
  Output 08 [Surround Left]
  Output 09 [Surround Right]
  Output 10 [PCM Capture Left]
  Output 11 [PCM Capture Right]
  Output 12 [MIC Capture]
  Output 13 [AC97 Surround Left]
  Output 14 [AC97 Surround Right]
  Output 15 [???]
  Output 16 [???]
  Output 17 [Analog Center]
  Output 18 [Analog LFE]
  Output 19 [???]
  Output 20 [???]
  Output 21 [???]
  Output 22 [???]
  Output 23 [???]
  Output 24 [???]
  Output 25 [???]
  Output 26 [???]
  Output 27 [???]
  Output 28 [???]
  Output 29 [???]
  Output 30 [???]
  Output 31 [???]




How to make those

---


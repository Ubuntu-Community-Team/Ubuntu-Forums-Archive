---
title: "No audio over HDMI with open drivers"
date: 2010-08-22
forum: Multimedia Software
---

### Post by OmegaWarrior on 2010-08-22
Problem:
I cannot get any output over the HDMI port of my ATi Radeon HD 4670 card with open drivers.  I tried using the proprietary drivers, and was able to get the audio working with those, but the video performance was lousy.  I have tried adding myself to the sound group with no change, and when I select "Digital Stereo (HDMI) Output" in the Hardware tab of the sound preferences menu, it simply reverts back to "Internal Audio" when I reopen it.  

aplay -l gives the following output:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have consulted multiple references and forum threads with zero luck; please, I have been struggling with this for months, does anyone know how to diagnose/solve this issue?

Specs:
My CPU is an Athlon64 x2 3800+
The video card is an ATI Radeon HD 4670 with 1GB of DDR3, output to a 42" Toshiba Regza TV over HDMI (1080p) and is in a PCIe 2.0 slot.
The system has 2GB of DDR2 RAM
Running Ubuntu 10.4 (Lucid Lynx)

Thank You

---


---
title: "Stream audio from iPod touch/iPhone over bluetooth to computer"
date: 2010-10-24
forum: Multimedia Software
---

### Post by Nephilime on 2010-10-24
I'm trying to stream audio from my iPhone 3GS iOS 4.01 to my linux computer via Bluetooth and A2DP.

**My setup:**
Bluez 4.69

pulseaudio 0.9.21

The stream actually works, but every 1/2 seconds there is a glitch in   the audio. Sometimes there are pitches in the audio. The audio is being   streamed at 44.1Khz and my phone is in an acceptable range of the   bluetooth enabled computer.

Pulseaudio outputs about every 5 seconds:

I: module-loopback.c: Should buffer 36012 bytes, buffered at minimum 92178 bytes
I: module-loopback.c: Old rate 45022 Hz, new rate 45046 Hz
I: module-loopback.c: Loopback overall latency is 63.33 ms + 352.51 ms + 39.51 ms = 455.35 ms

I load the loopback module as follows:

*pactl load-module module-loopback   source=bluez_source.00_26_B0_8D_6F_39   sink=alsa_output.usb-Native_Instruments_Audio_2_DJ_SN-v42x7kbg-00-Audio2DJ.analog-stereo   rate=44100*

Does anybody have a clue or direction to solve this issue? Thanks in advance!

---


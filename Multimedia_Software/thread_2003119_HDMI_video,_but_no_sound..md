---
title: "HDMI video, but no sound."
date: 2012-06-13
forum: Multimedia Software
---

### Post by vande700 on 2012-06-13
Hi all,

First off, I'd like to say I checked high and low for any possible solutions, but alas, I found none. 

I am currently unable to get sound out of my hdmi connected tv. I do get picture though. When I had 11.10, it came up in the sound settings and all I had to do was select it. Now when I connect it, HDMI is not even listed.

I'm using an acer 6920 with the nvidia geforce 9500m (512mb). I've tried reinstalling the video drivers and still no luck. 

I'll provide any log files that are needed, just please provide terminal code (going on 4 months now of using ubuntu). 

Thanks for your time

---

### Post by vande700 on 2012-06-18
bump

---

### Post by BicyclerBoy on 2012-06-18
AFAIK Your graphics cards (on-board 9500m) does not support full HDMI HDA audio. So you do not see HDMI audio codecs listed in sound control.

This type of HDMI audio is called pre-azalia & supports audio as stereo PCM & AC3 & DTS.
Most modern TVs work PCM & AC3.
The max PCM bitrate could be 48KHz.

Better audio control is via pavucontrol, the std sound control is a bit lost.

Because you had sound working previously on same h/w..
The GPU must support IEC958 over HDMI..this output is the mobo soundcard output re-routed over the HDMI link instead of S/PDIF.

aplay -l
look for digital sub-device

try
speaker-test -l 4 -c 2 -r 48000 -D hw:0,1
or
speaker-test -l 4 -c 2 -r 48000 -D iec958

---

### Post by vande700 on 2012-07-29
so is there any possible solution to getting this to work?

---

### Post by BicyclerBoy on 2012-08-03
Some pre-azalia GPUs can route the on-board/chipset audio codec thru' HDMI as SPDIF..so stereo PCM & pass-thru' AC3/DTS..

Did you try pavucontrol ?

Did you try the speaker-test debugging ?

---

### Post by cy bais on 2012-08-04
I'm in the same boat. Here's my output for the above tests.

Ubuntu 12.04 (Acer Aspire) 

==
ali@miyagi: aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ali@miyagi:  speaker-test -l 4 -c 2 -r 48000 -D hw:0,1

speaker-test 1.0.25

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -2,No such file or directory
==

---


---
title: "[SOLVED] Problem capturing audio under Pulseaudio"
date: 2008-05-16
forum: Multimedia Software
---

### Post by alfonsett on 2008-05-16
I'm posting this hoping someone will be so kind to give me a hint.

I have an "Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)" onboard sound card. ALSA detects a Realtek ALC882 Analog (DUPLEX) codec (ALC885 under alsamixer), although I've got an ALC889 codec on my Gigabyte P35-S3 mainboard. I'm running Ubuntu 8.04 with Pulseaudio enabled and set as a default for both audio output and capture.

I want to record what goes through my stereo speakers.

When I check the capture levels while playin some audio through Rhythmbox, everything looks fine (the bars are moving up and down under pavumeter). The default sample format is float32le, 2-channel, 44100Hz. Pavucontrol shows "Monitor Source of ALSA PCM on front:0 (ALC882 Analog) via DMA" as an input device, which is set as default. The Gnome volume applet lets me set the volume of the master Pulseaudio channel, and when I move the slider, the bars of pavumeter reflect the volume change.

However, when I open gnome-sound-recorder, hit "Record" while music is playing and everything is looking just right, wait for some seconds, hit "Stop" and then "Play", I don't hear anything. Gnome-sound-recorder hasn't recorded anything!

I have tried to capture audio with audacity, but still no success.

What am I doing wrong? Is it my fault? Or does Ubuntu not have the latest version of ALSA? I've read at ALSA's website that support for the ALC889 audio codec was introduced with version 1.0.16. Some of the ALSA libraries on my updated (18.05.2008 ) system have version 1.0.16, others 1.0.15...

When I open Gnome's multimedia configuration utility and test the audio capture device, I can only hear something for one second; after that the sound chops and disappears.

I've been looking everywhere for somebody with the same problem. I've tried OSS4, ALSA with no Pulseaudio, a custom .asoundrc... All that didn't help.

I hope somebody can help me with this issue. Thanks!

---

### Post by alfonsett on 2008-05-17
I've found the solution myself.

All I had to do was to install the audio driver package v5.03 from Realtek's website (version as of 2008/05/15).

I needed Ubuntu's build tools + ncurses-dev + gettext to get all the source code compiled and alsaconf running, but now my card is capturing sound correctly.

---


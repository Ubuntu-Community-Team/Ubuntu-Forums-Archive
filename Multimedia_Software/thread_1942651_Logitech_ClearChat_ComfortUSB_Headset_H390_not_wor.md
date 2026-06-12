---
title: "Logitech ClearChat ComfortUSB Headset H390 not working on elementary OS Jupiter"
date: 2012-03-18
forum: Multimedia Software
---

### Post by warm cardigan on 2012-03-18
Hello,

I am running elementary OS Jupiter, which is based on Ubuntu 10.10. elementary seems incapable of correctly recognizing my Logitech ClearChat Comfort USB Headset. The headset shows up in System > Preferences > Sound > Output, but only produces audio so low that it is almost inaudible. 

I have tried a number of things - different outputs, etc. Nothing seems to be working.

Has anyone else encountered a problem similar to this?

R3nCi

---

### Post by Rodney9 on 2012-03-18
sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Thanks To ZekeGraal

---

### Post by warm cardigan on 2012-03-18
Thank you very much, problem solved.

---


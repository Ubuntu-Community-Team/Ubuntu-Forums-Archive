---
title: "PulseAudio default source entry lost. Why?"
date: 2010-01-13
forum: Multimedia Software
---

### Post by Robbyx on 2010-01-13
I set up my webcam mic as the default source within the PulseAudio Manager. It worked and I restarted the computer. The first time on reloading there was no longer any  entry in the default source name field but PA did use the webcam for sound. However it lost the video and could not see the camera. I restarted the computer. This time it found the video and could use it. The default entry for the PA source is still not showing there, even though the sound source is defaulting to the mic in the webcam. 


Does anyone know how to ensure that the default sound source remains allocated and showing in the setup for defaults within the PulseAudio manager?

---

### Post by _geo on 2011-01-13
I get a similar problem. It only seems to happen if I re-route the input  to another application, after that I can't get the mic input back. The  only way to restore it is to kill pulseaudio and restart any programs  that use it.

---


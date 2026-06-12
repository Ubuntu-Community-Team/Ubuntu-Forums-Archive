---
title: "x-fi + best sinc interpolation + 96/48khz 24bit how?"
date: 2010-03-24
forum: Multimedia Software
---

### Post by gracchus on 2010-03-24
Hi,

I've read this forum a lot in the past but I finally registered so I could post a question.

How would I get alsa and libsamplerate to use the "best sinc interpolation" to output 96/48khz 24bit to my x-fi xtreme music on 9.10 karmic.  I think alsa uses "fastest sinc interpolation" as the default.

Thanks

---

### Post by gracchus on 2010-03-24
Found the answer here:
[http://ubuntu.sun.ac.za/wiki/index.php/HardwareAudio](http://ubuntu.sun.ac.za/wiki/index.php/HardwareAudio)

Edit the pulseaudio config:> gksudo gedit /etc/pulse/daemon.confEdit these lines:> resample-method = src-sinc-best-quality> default-sample-format = s24le> default-sample-rate = 96000Correct me please if I'm wrong.  

Does rythmnbox use pulseaudio or do I need to use a different media player like xmms?

---


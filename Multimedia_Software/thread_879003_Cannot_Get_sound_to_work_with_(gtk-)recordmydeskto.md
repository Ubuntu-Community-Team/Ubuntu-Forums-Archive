---
title: "Cannot Get sound to work with (gtk-)recordmydesktop"
date: 2008-08-03
forum: Multimedia Software
---

### Post by DeltaUK on 2008-08-03
hey i am using an X-Fi on OSS which works ok
recordmydesktop states it can support alsa and oss but i cant get it to work still, there is no option to switch it to oss. i get error 768 

Initial recording window is set to:
X:0   Y:0    Width:1440    Height:900
Adjusted recording window is set to:
X:0   Y:2    Width:1440    Height:896
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
ALSA lib pcm_hw.c:1207:(_snd_pcm_hw_open) Invalid value for card
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.


how do i force it to use oss?

thx

*more info - ubuntu 8.04.1 64bit installed from windows with wubi

---


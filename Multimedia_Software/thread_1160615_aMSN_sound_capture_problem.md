---
title: "aMSN sound capture problem"
date: 2009-05-15
forum: Multimedia Software
---

### Post by parazythum on 2009-05-15
Hi there,

I have a weird problem with AMSN : I can't capture sound from my webcam, a Quickcam Communicate STX. I'm under Ubuntu 8.10.

In Ubuntu, System/Preferences/Sound, I set the sound capture to the USB sound device. When I use the Sound Recorder, the sound capture is OK (capture and playback, I can hear my voice). My USB sound capture device is listed twice in the sound preferences, alsa and OSS. In the Sound Recorder, sound capture only works with Alsa, not OSS.

In aMSN, I capture the video, no problem, so my webcam is really recognized. For the sound capture, I have /dev/dsp and /dev/audio listed as possible record sources, but none works : the recorded sound is flat.

I tried to set the sound server to everything I could (searched a lot with Google), but none works (aplay $sound, paplay $sound, etc, even with the snack library, which is installed on my system).

I already spent 3 hours on that problem. Any idea ?

---


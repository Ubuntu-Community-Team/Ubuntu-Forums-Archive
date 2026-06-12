---
title: "Sound gets stuck with external usb soundcard on ubuntu 14.04"
date: 2014-06-16
forum: Multimedia Software
---

### Post by arts2 on 2014-06-16
I recently upgraded to ubuntu 14.04, and now my audioplaying gets stuck on the first frame when using an external soundcard (Roland Quadcapture). Support was added to kernel 3.11. The soundcard worked fine on ubuntu 13.10. I tried also using the old kernel from the 13.10 installation without success, so it seems to be ubuntu 14.04 configuration issue.

Tried playing with:
aplay -D default:CARD=QUADCAPTURE file.wav
which just freezes, mplayer file.wav displays:
AO: [pulse] 44100Hz 2ch s32le (4 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 321.0 (05:21.0) ??,?% 
Audio device got stuck!
A:   0.4 (00.3) of 321.0 (05:21.0) ??,?% 
Audio device got stuck!
...
and continues to spam the same message. Other sound-devices work as expected.

Here is my alsa-info: [http://www.alsa-project.org/db/?f=1e8cdaf4c04b39c4277edaecfd79301d823c07fe](http://www.alsa-project.org/db/?f=1e8cdaf4c04b39c4277edaecfd79301d823c07fe)

---


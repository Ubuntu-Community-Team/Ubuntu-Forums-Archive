---
title: "USB Audio works, but not unless I unplug/replug"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by BatsShadow on 2007-07-29
I have a Lexicon Alpha USB audio device.  I would like to use it with Ardour/Jack, but I would also like to use it for all my system audio.

When I boot, the light on the front of the Alpha is not lit up and no audio will play.  If I unplug/replug, then the light turns on and audio works correctly.

I started following the Comprehensive Audio guide, and

aplay -l

does correctly show my sound card even when it is unlit/not working:

**** List of PLAYBACK Hardware Devices ****
card 0: Alpha [Lexicon Alpha], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any suggestions on how to get the device to work on boot?

---


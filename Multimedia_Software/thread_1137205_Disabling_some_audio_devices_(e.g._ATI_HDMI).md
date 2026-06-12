---
title: "Disabling some audio devices (e.g.: ATI HDMI)"
date: 2009-04-25
forum: Multimedia Software
---

### Post by yankeeDDL on 2009-04-25
Hello,
I'm trying to setup a bluetooth headset to use with Skype.
While doing so, I realize that I have a lot of audio modules available which I don't need.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don;t use/need ATI HDMI audio. I don't even know how would I use it.
Also, I don't care to have both the analog and the digital nvidia device: I only use the analog out.

Is there a way to disable these two?

What's particularly annoying is that each device generates 2 entries in Skype audio. As a result, I have a long list of choices every time I want to modify the audio options ...

Thanks.

---


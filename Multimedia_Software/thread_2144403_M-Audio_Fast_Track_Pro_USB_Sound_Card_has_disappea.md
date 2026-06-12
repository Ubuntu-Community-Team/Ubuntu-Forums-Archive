---
title: "M-Audio Fast Track Pro USB Sound Card has disappeared. Can I try again?"
date: 2013-05-12
forum: Multimedia Software
---

### Post by BadElvis on 2013-05-12
Hi Ubuntu Forums,

I have this USB sound device: M-Audio Fast Track Pro. I once had it working with Ubuntu, only default settings, no special real-time kernel or anything fancy. Now I reinstalled Ubuntu and when I plugged the FTP into the USB port originally, its 2 channels showed up as output devices in the sound configuration of Ubuntu. I selected one of them and made some setting in a drop-down box (something like 'Channel A Stereo Output'). I played around a little and suddenly the device vanished from the list of output devices. Ok, so I tried with the second channel and managed to have this one removed as well. Now the output devices are gone and even if I replug the FTP, they do not reappear. I only got the built-in audio device now:

[http://s17.postimg.org/6mga9mxcb](http://postimg.org/image/6mga9mxcb/)

I know that the FTp can be configured with these settings somehow, because I had it running with the last install. Unfortunately, the settings are now messed up! How can I remove any configuration data, that might be related to the M-Audio Fast Track Pro? I hope, that when this data is removed, the device will show up in the list of devices like it did when I first connected it. My question is, where are those files? How can I delete them?

Thanks in advance for any help!

Note: 'aplay -l' shows the two channels of the sound card:
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---


---
title: "Sound not working despite all efforts"
date: 2009-07-14
forum: Multimedia Software
---

### Post by Urgoz on 2009-07-14
I recently installed Ubuntu 9.04 from Wubi and I was pretty psyched. However, I have two problems, one being that my sound is not working. Ubuntu recognises my sound card but refuses to play any audio. I followed the comprehensive guide in this forum but I'm still having problems.


> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ben@ubuntu:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
	Subsystem: Dell Device 0230
	Flags: bus master, 66MHz, medium devsel, latency 64



I'm not sure if that Terminal command helps at all or not. If anyone needs any more information or has any solutions then that'd be great. 
I've only used Ubuntu for about a half-hour so I'm definitely a beginner, hehe.

Thanks.

---

### Post by igorzwx on 2009-07-15
If nothing helps, you may try OSS4
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

But HDA might be a problem.
USB audio devices are not supported by OSS4,
and something else too

---


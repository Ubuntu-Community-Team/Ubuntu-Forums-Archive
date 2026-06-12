---
title: "Need help getting stereo output over SPDIF (ac3 is fine!)"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Rikko on 2009-05-03
Last week I thought I'd take the plunge and move to Ubuntu on my media center. Almost everything worked out of the box but I've still got a lingering audio issue that is a show stopper. I'm certain it's just a config issue but I'm too much of a Linux dummy to properly understand everything that's going on.

Hardware specs:
ASUS P5B-VM DO motherboard with onboard audio and optional SPDIF module installed.
Connected to 5.1 receiver via optical cable
(any other hardware relevant?)

OS:
9.04 64 bit edition (vanilla install)

I was able to get the drivers installed (or they were already there... I've been around and around this issue a few times :) ).

Results of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

my ultimate goal is to run Boxee or XBMC so it is my understanding that I just have to get everything playing nice in MPlayer. Almost there...

When I play an ac3-encoded video in MPlayer or XBMC it works great (though in MPlayer I do get a modal error about the sound, but it plays fine). 
When I play a stereo video (or any system sound) I get nothing.


I already ran alsamixer and unmuted all channels, so at this point I think I just have a conf file misconfigured.


I just want stereo sound to work - I don't care if it's only coming out of the front speakers< cloned to the rear channels< or even bloody mono! 

If someone wouldn't mind taking me through the 20 questions game I would really appreciate it. I was able to find a few threads but most people either had the opposite problem (only stereo worling) or their solution didn't match my issue.


Thanks!

---

### Post by Rikko on 2009-05-24
Ah, got it.
It's an ALSA bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632)

There's a workaround posted by Jean Francois about halfway down the page that seems to have done the trick.

---

### Post by jason32835 on 2009-10-07
Yes! Thank you for posting your solution. Works like a charm. You rock!

---


---
title: "Microphone distortion"
date: 2012-06-19
forum: Multimedia Software
---

### Post by okon3 on 2012-06-19
Hi all!
I'm trying to get my microphone to work but i cant!
I'm using Kubuntu 12.04 btw the problem is the same also with 11.11 and 11.04 (ubuntu, xubuntu and kubuntu)

The distortion is this one

[http://regazzi.web.cs.unibo.it/helloeveryone.wav](http://regazzi.web.cs.unibo.it/helloeveryone.wav)

And here are some outputs

```
okon3@bingobongo2:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

```
okon3@bingobongo2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
okon3@bingobongo2:~$ 

```

i've already googled a lot and still cant find a solution :(

my laptop is an hannspree sn12

thanks in advance, feel free so ask for any output :D

---


---
title: "Feedback(?) Noise when System Capture and Playback are Connected"
date: 2009-10-06
forum: Multimedia Software
---

### Post by prasadbrg on 2009-10-06
Hello everyone, 
  Ive been using my Compaq Presario laptop (2.4 GHz Celeron, 1 GB ram), running Xubuntu 9.04, for live music performances, for the past 4 months or so. All my applications are routed through QJackCtl. I process audio coming in through the mics through a couple of applications. 
  A few days back, when I started qjackctl, there was this awfully loud noise. To isolate the problem, I closed one application after the other - and to my surprise, the issue would persist even when there were no applications that used Jack. All it needs is for the 'capture' ports to be connected to the 'playback' ports. The noise disappears when I disconnect these. The noise is also present when the connection from capture to playback is indirect (which was default when I noticed the problem): capture->jack-rack; jack-rack->playback.
The 'capture' ports refer to my mic inputs. However, the noise persists even when the mics are *not* plugged in! Also, in the mixer (xfce4-mixer/alsamixer), I find that the noise is not affected by the mic volume, instead, it only increases/decreases with the PCM level.
  On a side note, around the same time, I also started having troubles with alsa, which periodicaly dies, requiring a force-reload, as described [here]("http://ubuntuforums.org/showthread.php?t=1257798&highlight=alsa+force-reload").
  I can't remember any major changes I made to my system around the time I first noticed the problem, but I'm sure I allowed the update-manager to install latest versions of packages around that time.
Any help would be appreciated! Thanks in advance...
Cheers,

Guru

P.S. I'm not sure what hardware info is needed, but here goes:
```
$ lspci -v | grep -i audio
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31

```

---


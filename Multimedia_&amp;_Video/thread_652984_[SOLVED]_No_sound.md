---
title: "[SOLVED] No sound"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by merike on 2007-12-29
I had sound after install, but at the moment it's completely missing. I first noticed it in Amarok by getting: "Audio output unavailable; the device is busy.
xine parameters: ", but when I went to Kubuntu System Settings I can't hear the test sound as well. The last change to media software that I can think of was installing some libraries for dvd playback. I didn't check then but I believe sound had to work then if I could hear sound from DVD.
There have been some system updates meanwhile but I don't know when it last worked.

---

### Post by icheyne on 2007-12-29
Try the troubleshooters here:

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by merike on 2007-12-29
For some reason I find those troubleshooters and debugging guide somewhat confusing.
Here's what I could understand:

From lspci:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
```
From both KMix and alsamixer I see that it is not muted. In fact even keyboard shortcuts for in/decreasing volume work, but there's no sound.
From System Settings I also checked that I am a member of audio group.
From aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Please ask for any other information that could help.

---

### Post by merike on 2007-12-29
Apparently you're not supposed to disable modem from BIOS on a Thinkpad X60s if you want to have sound. Thank god we have Thinkwiki!
Is there a guide for improving sound quality? I feel that the same combination of soundcard and speakers sounds somewhat better under Windows than in Kubuntu.

---


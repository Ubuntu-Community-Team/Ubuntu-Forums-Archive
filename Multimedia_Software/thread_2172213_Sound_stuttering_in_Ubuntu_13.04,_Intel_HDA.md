---
title: "Sound stuttering in Ubuntu 13.04, Intel HDA"
date: 2013-09-03
forum: Multimedia Software
---

### Post by Ekkoria on 2013-09-03
Hi,
My audio is occasionally (~every five minutes, give or take) stuttering - it either quits completely, or repeats about half a second of the sound that came before and then skipping ahead. It only happens for a split second, but it's getting quite irritating. It happens when using the regular audio output, but I'm not sure if it happens using the HDMI output my laptop has; I don't think so but I don't usually use that output. It happens when using Rhythmbox and Chrome, so I'm pretty sure it's a driver issue or something rather than a particular program because the issue is exactly the same across both.
Here's some info on my sound card, not sure if this will be helpful or not:
```
evan@laptop-e:~$ sudo lspci -v | grep -A7 -i "audio" 
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 1b43
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at dfe00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
evan@laptop-e:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Yellow Pasque on 2013-09-03
Try latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If that doesn't solve it, see: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

If that doesn't work, pray.

---

### Post by Ekkoria on 2013-09-04
I've already tried the PositionReporting fix, which didn't help. However I installed the latest driver a couple hours ago and everything seems to be going well, so if the issue doesn't occur again within a couple days I'll call it solved. For now, I'm praying.

---

### Post by Ekkoria on 2013-09-04
The gods of audio have frowned upon me, and my prayers to them aren't having any effect. Now what?

---

### Post by Yellow Pasque on 2013-09-04
```
ubuntu-bug audio
```

---


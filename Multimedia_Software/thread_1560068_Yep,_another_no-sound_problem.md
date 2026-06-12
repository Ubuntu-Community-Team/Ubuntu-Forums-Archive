---
title: "Yep, another no-sound problem"
date: 2010-08-24
forum: Multimedia Software
---

### Post by fluidz on 2010-08-24
So, here's the thing: i've got a HP dc5800 with Ubuntu 10.04 with no sound whatsoever. I've already tried every single method out there and none were successful. It says my card is a HDMI even though my pc does not have an HDMI port. If anyone have ever seen something like that i would really apreciate some help. Here are some info that may be useful:

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


dmesg | grep HDA
```
[    9.578559] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.578627] HDA Intel 0000:01:00.1: irq 28 for MSI/MSI-X
[    9.578647] HDA Intel 0000:01:00.1: setting latency timer to 64
```

lspci -v
```
01:00.1 Audio device: ATI Technologies Inc RV710/730
        Subsystem: XFX Pine Group Inc. Device aa38
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Memory at f0110000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```
And my alsa info: [http://www.alsa-project.org/db/?f=7bf09ea553533440f4dbb73a6c2dc0ce28ac2f3b](http://www.alsa-project.org/db/?f=7bf09ea553533440f4dbb73a6c2dc0ce28ac2f3b)

---

### Post by lidex on 2010-08-28
Remove the custom entries you made in alsa-base.conf and reboot.

---


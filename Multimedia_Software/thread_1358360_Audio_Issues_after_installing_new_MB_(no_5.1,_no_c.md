---
title: "Audio Issues after installing new M/B (no 5.1, no capture)"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Thomas Kenobi on 2009-12-18
After installing new hardware components (new CPU, M/B, RAM, GPU), I've been having some issues with sound in Karmic. Specifically, I have no 5.1 functionality, though the two front speakers and the subwoofer are working, and no capture functionality. I had similar issues with Win7, but installing the latest audio drivers from the Asus website fixed those issues and now everything is working fine. However, in Linux, I haven't been able to find a similarly straightforward solution.

To describe the issue in a bit more detail:

I didn't reinstall either OS after installing the new hardware components.

The new M/B is: Asus P7P55D
Audio Chipset: VIA VT1828S 8-channel HDA Codec

```

&aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

``````

&lspci -v

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8375
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

``````

&alsamixer

Card: HDA Intel
Chip: VIA ID 4441

```Inside alsamixer I see only the following channels:
[Playback] -> Master, PCM
[Capture] -> Capture

I've followed the instructions in this page [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) up and to the point of recompiling the ALSA driver from source, but I've seen no improvement.

The obvious: I checked to see if the capture channel was muted and I also checked the hardware page of the sound preferences gui. The card is identified as "Internal Audio" and the only options available there are "Off, Analog Stereo Input, Analog Stero Output, Analog Stereo Duplex". No mention of 5.1.

Any help would be welcome, because I'm not sure what else to attempt.

---

### Post by Thomas Kenobi on 2009-12-18
The problem was fixed by, first following the advice here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359)

and then running the commands from the "Getting the ALSA drivers from a *fresh* kernel" chapter here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---


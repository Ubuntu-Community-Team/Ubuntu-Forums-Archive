---
title: "Garbled sound 8.04 LTS"
date: 2009-02-13
forum: Multimedia Software
---

### Post by lukedupree on 2009-02-13
Hi All

I have been trying to get past this sound issue for a couple of months off and on with NO success. I have performed clean install of 8.04 Hardy a few times, update sound drivers, went through the definitive guide, installed ALSA drivers, and so on. Since I am pretty new to Linux in general and Ubuntu I am shooting the dark a great deal of the time.

This sound: attached

I have tried the following:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

[http://ubuntuforums.org/showthread.php?t=885437&highlight=list+hardware](http://ubuntuforums.org/showthread.php?t=885437&highlight=list+hardware)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


# aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

# lspci -v

00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82fe
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

Says <access denied> not sure if that is significant.

I have tried so many things I now have no idea what configuration and settings actually exist.

At the time of this posting I am going through the

Comprehensive Sound Problem Solutions Guide v0.5e

yet again to try and resolve this.

If anyone can help I'm all ears.

Thanks

Luke

---

### Post by Stochastic on 2009-02-14
Moved to Multimedia & Video.

Bump.

---


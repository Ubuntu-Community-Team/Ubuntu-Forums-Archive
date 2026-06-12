---
title: "No sound in 12.04"
date: 2012-05-06
forum: Multimedia Software
---

### Post by Lars Noodén on 2012-05-06
I've got no sound in 12.04.  I've tried these instructions in an attempt to get sound:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

This produces no sound:
```

aplay /usr/share/sounds/alsa/Front_Center.wav

```

aplay has the following output

```

 sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Speaker [Logitech USB Speaker], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci has the following output

```

$ lspci -v | grep -A7 -i audio
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at d3480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

```

I've had sound before on this machine, back under 11.10 but the fresh install of 12.04 leaves it without sound.

---

### Post by Krunoslav on 2012-05-06
I have the same problem , i even tray to add Sound card from another comp but with no results .. :(

---


---
title: "No sound"
date: 2012-06-13
forum: Multimedia Software
---

### Post by Tikhon03 on 2012-06-13
When I first installed Ubuntu I had sound, then lost it when upgrading to a newer version.  I found a temporary fix, which stopped working in a later update, and haven't found anything that worked since then.  If someone could help me that would be great.  Thank you.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
dmesg | grep HDA
[   12.532544] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   12.532675] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   12.532785] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   12.532893] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.533004] input: HDA Intel PCH Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.533110] input: HDA Intel PCH Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.533218] input: HDA Intel PCH Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.533323] input: HDA Intel PCH Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.446651] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   13.446732] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   13.446797] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   13.446859] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
``````
 lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: Micro-Star International Co., Ltd. Device 7681
        Flags: bus master, fast devsel, latency 0, IRQ 57
        Memory at fb400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

--
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
        Subsystem: NVIDIA Corporation Device 0828
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fb080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

```

---


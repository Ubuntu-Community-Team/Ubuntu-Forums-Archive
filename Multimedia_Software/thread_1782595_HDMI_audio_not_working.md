---
title: "HDMI audio not working"
date: 2011-06-14
forum: Multimedia Software
---

### Post by Tiddens on 2011-06-14
Have reviewed all related posts and tried everything.  Appreciate your help!

System:  AMD Athlon II Neo Processor K125 with Nvidia nForce 9200 Chipset

Ubuntu 9.10

Analog output works fine.

I can access options and choose HDMI in System/Preferences/Sound.

alsamixer shows Card: HDA Nvidia, Chip: Nvidia MCP78 HDMI

lspc -v (audio output portion)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0448
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fbf78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm trying to graduate from Ubuntu "beginner".  Can do anything you tell me to try.

Thank you in advance!

---

### Post by BicyclerBoy on 2011-06-14
To get HDMI audio working you need video driver support & alsa driver (kernel module) support.

According to the nvidia hdmi document..
there was an important bug fix for MCP89 & MCP7x GPUs that only got into kernel 2.6.34.2 & 2.6.35.
[But maybe this bug has no effect on you]
Stock std. Lucid 10.04 is still kernel 2.6.32.33.
I'm not sure what nvidia graphics driver version is required.
People did seem to get MCP78 HDMI audio with Karmic 9.10 & nvidia 195 somehow..

The general consensus is that alsa 1.0.24 seems to solve most HDMI problems but this could be overkill.

If you want to stay at 9.10 you may have problems finding any ppa with up-to-date nvidia drivers & alsa modules backports..
I think there is more support for 10.04 because it is LTS..

---


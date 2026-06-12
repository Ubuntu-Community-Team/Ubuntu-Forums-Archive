---
title: "Intermittent sound issues while playing video"
date: 2011-07-28
forum: Multimedia Software
---

### Post by CVGH on 2011-07-28
Hi Folks,

Sometimes while playing a video the spoken audio is very low, yet the sound effects/music are so loud you can't make out the speech.
Sometimes the audio just isn't there at all or very low.
This happens with VLC or Miro.
```
20:54:07 lister@jupitermining:~$ lspci -v00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
    Subsystem: Dell Device 0189
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ed00 [size=256]
    I/O ports at ec40 [size=64]
    Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
    Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

``````
18:32:34 lister@jupitermining:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
18:32:12 lister@jupitermining:~$ pulseaudio --version
pulseaudio 0.9.21-63-gd3efa-dirty

```If reboot and open the same file in VLC, works fine!

Is this a ALSA or Pulseaudio problem?

Thanks!

---


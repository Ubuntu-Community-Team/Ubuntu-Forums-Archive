---
title: "no sound from left hand speaker"
date: 2010-08-04
forum: Multimedia Software
---

### Post by icodemonkey on 2010-08-04
Need Help I recenltly added a Radeon 9550 AGP card to my system and now I can only get sound out of the right speaker (usb powered stereo speakers).

no idea how to get the left speker to play sound. I know it works as i have it pluged in to my mp3 player

output of: aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```output of: lspci -v
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 12bc
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 2000 [size=256]
    I/O ports at 2400 [size=64]
    Memory at f0b00400 (32-bit, non-prefetchable) [size=512]
    Memory at f0b00600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
```is that enough info or do i need more if so what

---


---
title: "followed Comp Sound Problem Solutions Guide help?"
date: 2009-12-19
forum: Multimedia Software
---

### Post by r-j on 2009-12-19
fresh install of U-Studio Karmic 9.10, dual boot sys. M-Audio 1010LT works fine in WinXP.

(1) aplay seems to nail the card:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

(2) lspci finds the appropriate ALSA entry:
```
04:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d63b
    Flags: bus master, medium devsel, latency 32, IRQ 21
    I/O ports at 10c0 [size=32]
    I/O ports at 10f0 [size=16]
    I/O ports at 10e0 [size=16]
    I/O ports at 1080 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712
```

(3) ALSA driver exists

(4)```
 sudo modprobe snd-ice1712
```

```
sudo nano /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
snd-ice1712
```

section: Using Alsamixer

Card:M Audio Delta 1010LT
Chip:ICE1712 - multitrack
view:[Playback]

I've brought up levels to reasonable levels,the section labeled "multi" is the only section I can mute/unmute with the "m" key.

I've tried playing clips from youtube and from audio Cd's, the volume on the taskbar is not muted, shows output 100%, 0.00db, ICE1712 (Envy24...blablabla)

if I open "Sound & Video > Pulseaudio volume control, nothing is muted and the VU's are bouncing!

so, why no sound, what am I missing????

my user name is in the audio group, if I unplug a playback the wire it is hot, so it is the OS right?
anybody? little help??


TY, RJ

---

### Post by lidex on 2009-12-20
Try this guide:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

---


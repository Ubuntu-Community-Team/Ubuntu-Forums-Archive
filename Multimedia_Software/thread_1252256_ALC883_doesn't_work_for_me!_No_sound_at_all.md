---
title: "ALC883 doesn't work for me! No sound at all"
date: 2009-08-28
forum: Multimedia Software
---

### Post by TraBruno on 2009-08-28
Hello all,

I just installed ubuntu 9.04 and don't get any sound out of it. My soundcard is Realtek ALC833. For some people it seems to work, but with me it does nothing. I already tried to reinstall ALSA, I unmuted everything I could in the alsamixer, but without succes. I found a solution that had to do with finding some codec on the ALSA configuration site, but I can't find anything relating to ALC833 so I'm stuck.

Does anyone have an idea?
Thanks in advance!

cat /proc/asound/card0/codec#* | grep Codec
```

Codec: Realtek ALC883
Codec: Motorola Si3054

```


aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Wistron Corp. Device 4071
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at d8440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---


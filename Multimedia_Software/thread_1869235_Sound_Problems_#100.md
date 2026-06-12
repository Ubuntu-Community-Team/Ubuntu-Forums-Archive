---
title: "Sound Problems #100"
date: 2011-10-25
forum: Multimedia Software
---

### Post by JohannesJo on 2011-10-25
Since a while i got no sound at the startup of 11.10. If I try to play a track in Banshee it crashes. But if I go to the Audio-Settings first in test my speakers, it suddenly starts working, although it might crash again from time to time. 

Sorry if this might be a double post, but I'm lacking the right search terms for this problems and in the more general threads I found nothing useful for me.


Does anybody have an idea what I might do to make it work properly?? I would be grateful!


### What might or might not be related: The Keyboard-Shortcuts i set for Banshee in the System-Settings dont work until i set them once more.

Some Data on my sound card (sry for the german output)

```

johannes@johannes-EasyNote-TJ65:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: CONEXANT Analog [CONEXANT Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: Conexant Digital [Conexant Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 7: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 8: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 9: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0


lspci -v

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0219
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f1500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel



```

---

### Post by JohannesJo on 2011-10-26
Nobody an idea? :-( Maybe I forgot to post something necessary?

One thing: My MP3-hard-disk is NTFS and automatically mounted at start-up.

---


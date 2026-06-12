---
title: "Disable onboard sound card"
date: 2010-03-13
forum: Multimedia Software
---

### Post by ursusca on 2010-03-13
Hello there!

Ubuntu 9.10
```
$ uname -a
Linux ubuntubear 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux
```

I have ASUS M4A78-E motherboard. I've disabled Onboard sound card (VIA VT1708S) and installed Audigy sound card (c-media sb 8738 5.1 channel (CMI8738/PCI-6ch-LX)). But my system still detects Onboard sound card.
```
$ alsamixer
AlsaMixer v1.0.20 (Press Escape to quit)
Card: HDA ATI HDMI
Chip: ATI RS690/780 HDMI
View:  Playback  Capture [ALL] 
Item: IEC958


``````
$ lspci
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
04:05.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

```

I've disabled HDA ATI HDMI in Gnome sound preference and i have perfect sound but my microphone is not working.

How can I fix this problem?

---

### Post by markbuntu on 2010-03-13
The ATI HDMI is part of the gpu and is a separate device from the on board sound. For the mic...check in the gnome mixer that the input is set to the audigy card and the mic is selected.

---

### Post by ursusca on 2010-03-15
> **markbuntu said:**
> The ATI HDMI is part of the gpu and is a separate device from the on board sound. For the mic...check in the gnome mixer that the input is set to the audigy card and the mic is selected.

Thanks for clarifying!

---


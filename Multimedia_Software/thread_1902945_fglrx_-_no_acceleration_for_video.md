---
title: "fglrx - no acceleration for video"
date: 2012-01-01
forum: Multimedia Software
---

### Post by observer1 on 2012-01-01
Hello everyone,

I have a problem with fglrx, which drives me nuts.
I use Ubuntu 11.10 and an ITX mainboard with AMD e350 APU (Output via HDMI).

It seems that when I play any video file in Totem or VLC, it won't use the GPU to process instead of the CPU.
When starting the video the CPU usage will go from idle to full immediately. The video shows artefacts and will stutter.
Bad for a machine which is intended to be our media pc.

I used the fglrx-drivers from Ubuntus "Additional Drivers" and tried a manual installation of fglrx.

Using the fglrx from Ubuntu I get:

Hardware (lspci):
```
00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
```fglrxinfo:
```
Display: :0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 4.1.11005 Compatibility Profile Context

```So IMHO everything looks crispy.

Does anybody have an idea what I missed?
Thanks in advance!

- obs-

---

### Post by MoreOrLess on 2012-01-01
You have to install xvba-video package, and use vlc to take advantage of it.

---

### Post by observer1 on 2012-01-01
> **MoreOrLess said:**
> You have to install xvba-video package, and use vlc to take advantage of it.

Just tried it (I guess you meant the package xvba-va-driver from multiverse), however nothing changed. Anything I need to enable in VLC afterwards?

---


---
title: "Mumble audio capture issue."
date: 2008-05-07
forum: Multimedia Software
---

### Post by DavidGX on 2008-05-07
I use a USB headset and have had nothing but crap getting ventrilo (using WINE and VirtualBox), teamspeak (native linux client and WINE) and now mumble to work properly. Right now I'm focusing on mumble.

Mumble installs and starts up perfectly. However when trying to configure the Input Device as soon as I select my USB headset under ALSA, it freezes.

I tried starting it in a terminal to see if anything interesting would appear, this is what I get..

> Locale is en_US
OpenSSL Support: 1
Overlay: Attempt for pixelsize 60 gave actual sizes 64.218750 -51.593750
Overlay: Attempt for pixelsize 59 gave actual sizes 63.156250 -50.734375
Overlay: Attempt for pixelsize 58 gave actual sizes 62.078125 -49.875000
Overlay: Attempt for pixelsize 57 gave actual sizes 61.015625 -49.015625
Overlay: Attempt for pixelsize 56 gave actual sizes 59.937500 -48.156250
Overlay: Attempt for pixelsize 55 gave actual sizes 58.875000 -47.296875
Overlay: Attempt for pixelsize 54 gave actual sizes 57.796875 -46.437500
Rescan!
GlobalShortcutX: Unable to open any input devices under /dev/input, falling back to XEVIE
Xlib:  extension "XEVIE" missing on display ":0.0".
GlobalShortcutX: XEVIE extension not found. Enable it in xorg.conf
ALSAAudioOutput: Initialized
ALSAAudioInput: Initing audiocapture default.
ALSAAudioInput: Actual buffer 1365 samples [341(320) per period]

Any ideas?

---

### Post by DavidGX on 2008-05-08
sporks

---


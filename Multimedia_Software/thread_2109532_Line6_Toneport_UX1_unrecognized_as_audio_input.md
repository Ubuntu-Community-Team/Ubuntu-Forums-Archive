---
title: "Line6 Toneport UX1 unrecognized as audio input"
date: 2013-01-27
forum: Multimedia Software
---

### Post by muzicmike on 2013-01-27
I have been trying very hard to get my Line6 Toneport to work with ubuntu 12.10.

I initially followed [these instructions]("http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html") to install the line6-usb drivers. When I got to System Preferences -> Sound, Ubuntu recognizes my UX1 as an audio output device (and it works as such) but it is not listed among the audio inputs.

Audacity recognizes the UX1 as an input, but when I try to record my guitar there is nothing.

What can I do to get Ubuntu to recognize my UX1 as an input device?


Alsamixer's "Capture" menu says 'This sound device does not have any capture controls'

Note: Would uninstalling the drivers from the above link work? I've read that the kernel already supports line6 devices but never tried it before the drivers install. If so, how do I uninstall them?

---

### Post by mdeitrick1991 on 2013-04-29
I noticed your post on AskUbuntu.com and had high hopes that I would find an answer here.  I've been having the same problems where Toneport UX1 is recognized as an output device, not an input device.

Since I too have not found a way to uninstall the drivers, the only thing I can recommend is using a utility called PulseAudio Volume Control.  However, this has not solved my problem (even though it lists Toneport as an input and output device).

---


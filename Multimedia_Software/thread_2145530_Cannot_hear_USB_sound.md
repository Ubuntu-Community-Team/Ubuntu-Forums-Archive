---
title: "Cannot hear USB sound"
date: 2013-05-15
forum: Multimedia Software
---

### Post by dargaud on 2013-05-15
Hello all,
I've been using a Asus uBoom USB speaker for a few years on an older laptop with Kubuntu 9 to 11. It worked out of the box but that computer died and got replaced by a HP Spectre on which I just installed 13.04.

The uBoom is detected but I cannot hear anything on it.
- in System Settings - Phonon - Audio Playback, I have the uBoom on top. Pressing [test] comes out of the internal speakers. Doing it on the internal works.
- in Audio Harware setup, if I select the uBoom and press [Front left]: silence
- in backend I've tried both GStreamer and VLC, no change.

There are no errors in dmesg, syslog or a pulseaudio log which I generated on purpose.

Any advice ?

---

### Post by dargaud on 2013-05-22
D'oh! The input jack was plugged into the uBoom and simply had priority over the USB sound. I'm brewing beer at the same time than I'm installing Ubuntu, so it may explain some failures on my part...

---


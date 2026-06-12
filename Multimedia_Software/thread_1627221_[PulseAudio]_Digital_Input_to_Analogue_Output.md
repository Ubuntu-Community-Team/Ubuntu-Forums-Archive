---
title: "[PulseAudio] Digital Input to Analogue Output"
date: 2010-11-21
forum: Multimedia Software
---

### Post by Aergan on 2010-11-21
Hi all,

I'm trying to get Digital Stereo Input to output to Analogue Output in Ubuntu 10.10 x64.

Source is S/PDIF TOSLINK IEC958 from Xbox 360 - > USB CM106 -> Analogue Surround 7.1 Speakers.

PulseAudio's Sound preferences will show that there is volume input over IEC958 and I can record it using Gnome Sound recorder.

Alsamixer will quite happily output analogue sources, but for IEC958 it only offers Capture via PCM. I've been told that I should be able to redirect a PulseAudio monitoring stream to output but I've no idea how to get this to work.

The USB CM106 will let me accomplish this in Windows 7 x64's Recording mixer, so I know the hardware can do it.

How can I tap into the digital input for listening?

---


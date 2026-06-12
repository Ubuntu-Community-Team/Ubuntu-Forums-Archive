---
title: "Can play sound but not record"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by whein on 2007-07-09
System specs:
AMD Athlon 64 X2 4400+ Toledo 2.2GHz Socket 939 Processor
ABIT KN8 Ultra Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard
EVGA 256-P2-N515-AX GeForce 7800GT 256MB GDDR3 PCI Express x16
Acer AL1917ABMD 19" 8ms DVI LCD Monitor
2x Hauppauge PVR-150MCE
Hauppauge PVR-350
running 7.04

Been fighting this for a while now.  I can play audio just fine from Myth, XMMS, GNOME startup, the little "ding" in the terminal.  But I cannot get any program to record sound!  I've tried Audacity, I've tried piping /dev/dsp and /dev/radio to a file, but it all comes out silent.  Tried messing with all the ALSA mixers and making sure nothing was muted on the control panels.  Ideally, I would like to be able to record any sound that is being played out of the speakers.  I'm trying to find a way to record the sound coming from the FM tuner in my PVR-350 since I cannot get any of the GUI based radio control programs to play it.  I'm forced to use the ```
ivtv-radio -f 94.5
``` command to listen to the radio, but then have no way to record it.  Ideas?  Suggestions?  Is there something goofy with that particular chipset on the motherboard?
-Will

---


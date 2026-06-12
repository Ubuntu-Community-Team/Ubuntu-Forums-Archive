---
title: "No volume control with CM8738"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by slackenerny on 2007-11-08
I just bought a new soundcard with a CM8738 chipset, to turn my server into some kind of jukebox. It's a gutsy **server** (so no KDE or gnome...)

Sound output seems to work (i can here music) but the left channel is louder than the right one, and whatever I do in alsamixer has no effect on what I hear. This holds for playback via mpg123 as well as for mpd. And that's pretty much all I can say, as I have no idea about sound under linux...
All I did so far was pluging in the card and adding the module (snd-cmipci).

Any ideas where I could start looking?

slackenerny

FYI:
```
lspci -v
        00:0d.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 12
        I/O ports at 9800 [size=256]
        Capabilities: [c0] Power Management version 2
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media PCI CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---


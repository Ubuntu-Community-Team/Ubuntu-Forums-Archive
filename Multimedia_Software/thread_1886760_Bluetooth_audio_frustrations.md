---
title: "Bluetooth audio frustrations"
date: 2011-11-25
forum: Multimedia Software
---

### Post by mauvebic on 2011-11-25
to use my android phone as an audio source for the computer i had to this:

```
pactl load-module module-loopback source=bluez_source.60_A1_0A_44_6E_55 sink=alsa_output.pci-0000_00_14.2.analog-stereo

```

even though in blueman theres a menu option to link up the audio source, though in pulseaudio, it appears under "record" rather than "playback".

What gives? any way to do this without resorting to the terminal? (or at least fix it once in the terminal)

Many thanks

---


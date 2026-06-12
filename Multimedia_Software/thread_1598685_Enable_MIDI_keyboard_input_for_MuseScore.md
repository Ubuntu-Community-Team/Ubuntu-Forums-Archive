---
title: "Enable MIDI keyboard input for MuseScore"
date: 2010-10-16
forum: Multimedia Software
---

### Post by brentsbaxter on 2010-10-16
Just purchased an M-audio KeyRig      49 keyboard to use with MuseScore 0.96 on my Ubuntu 10.04 desktop. I expected to just plug in to a USB port and start entering notes on the score.

Pressing the keys did nothing. Checking  /dev/sndstat I found

--------------
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux brent-desktop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xfbffc000 irq 16
Creative Technology Ltd VF0410 Live! Cam Video IM Pro at usb-0000:00:1d.7-2.1, 

Audio devices:
0: VT1708B Analog (DUPLEX)
1: USB Audio

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: VIA VT1708B 8-Ch
1: USB Mixer

-------------------------------------
I presume MIDI devices must be enabled, but I do not know how to do it.
Once this is done, is there more I need to do so MIDI keyboard input will with with MuseScore?

Brent

---


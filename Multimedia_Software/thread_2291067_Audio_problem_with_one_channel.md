---
title: "Audio problem with one channel"
date: 2015-08-17
forum: Multimedia Software
---

### Post by zkab on 2015-08-17
I have problem  with audio channels - only right channel is heard.
Here is what I have:

inxi -Fxz
System:    Host: zkab Kernel: 3.19.0-25-generic x86_64 (64 bit gcc: 4.9.2) Desktop: Xfce 4.12.0 (Gtk 2.24.27)
           Distro: Ubuntu 15.04 vivid
Machine:   Mobo: Gigabyte model: P55A-UD4 v: x.x Bios: Award v: F11 date: 05/03/2010
CPU:       Quad core Intel Core i7 870 (-HT-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 23451
           clock speeds: max: 2927 MHz 1: 1197 MHz 2: 1463 MHz 3: 1463 MHz 4: 1463 MHz 5: 1862 MHz 6: 1197 MHz
           7: 1330 MHz 8: 1596 MHz
Graphics:  Card: NVIDIA GT215 [GeForce GT 240] bus-ID: 01:00.0
           Display Server: X.Org 1.17.1 driver: nvidia Resolution: 1920x1200@60.0hz
           GLX Renderer: GeForce GT 240/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 340.76 Direct Rendering: Yes
Audio:     Card-1 Intel 5 Series/3400 Series High Definition Audio driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k3.19.0-25-generic

cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC889

I tested with [http://www.kozco.com/tech/LRMonoPhase4.wav](http://www.kozco.com/tech/LRMonoPhase4.wav) and to be sure there is nothing wrong with my amplifier & speakers I unplugged the phone connector 
from my Ubuntu box and plugged it into a Windows laptop - and it worked OK.
What could be the problem?

---


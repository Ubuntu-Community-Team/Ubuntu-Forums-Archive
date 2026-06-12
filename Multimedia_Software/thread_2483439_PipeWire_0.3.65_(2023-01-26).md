---
title: "PipeWire 0.3.65 (2023-01-26)"
date: 2023-01-30
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-01-30
When will we be able to download this fix for 22.10?

Please see [https://github.com/PipeWire/pipewire/blob/master/NEWS](https://github.com/PipeWire/pipewire/blob/master/NEWS)  (wtay 0.3.65).  I can get existing pipewire (0.3.58-2) to sometimes work on my DELL 7720 laptop, but the first step is waiting 20 minutes after logging in to start working with the PC and then opening Firefox and going to a webpage that has streaming internet radio and starting the playback.

John

---

### Post by cigtoxdoc on 2023-01-31
I got the problem solved (at least for now) by following instructions at [https://www.maketecheasier.com/install-configure-pipewire-linux/](https://www.maketecheasier.com/install-configure-pipewire-linux/) .  After following instructions, I got the following for pactl info

ohn@john-Precision-7720:~$ pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 191
Tile Size: 65472
User Name: john
Host Name: john-Precision-7720
Server Name: PulseAudio (on PipeWire 0.3.58)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1f.3.analog-stereo
Default Source: alsa_input.pci-0000_00_1f.3.analog-stereo
Cookie: 2aba:e98a
john@john-Precision-7720:~$

Before following the instructions, the Default source was "alsa_output"

John

---


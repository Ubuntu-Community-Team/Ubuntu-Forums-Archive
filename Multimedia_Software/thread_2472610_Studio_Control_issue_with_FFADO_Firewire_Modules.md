---
title: "Studio Control issue with FFADO Firewire Modules"
date: 2022-03-06
forum: Multimedia Software
---

### Post by jmb13 on 2022-03-06
Hello,
I'm running ubuntustudio 21.10 and studio control with FFADO Firewire Modules (sound device MOTU 828MKII). I have an annoying issue : If I configure JackMaster settings with main output ports other than system:playback_1 <firewire_pcm> studio control doesn't entirely starts. It hangs on "Adding Bridges". It runs but no connexions are made between pulse and jack. It is very annoying because the main output of my sound device are 11 and 13 (Main output). And for instance if I want to playback sounds in Audacity, portaudio connects to the first port of my device which is the headphones and not main output...

It seems to be a bug for me (there is no reason not to be able to start studio control on another main output than 1) but I don't know where to report bugs for studio control.

---


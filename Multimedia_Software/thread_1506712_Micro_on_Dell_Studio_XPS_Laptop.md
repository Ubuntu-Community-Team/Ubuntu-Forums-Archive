---
title: "Micro on Dell Studio XPS Laptop"
date: 2010-06-10
forum: Multimedia Software
---

### Post by arover on 2010-06-10
[RIGHT][/RIGHT]Hi,
I have some trouble to use the integrated microphone which is part of my webcam I guess.
Video capturing on my webcam works well but the integrated microphone don't.

I can't also use the standard input of my laptop sound card. Nothing append when I connect a microphone.

I test the microphone input with pavumeter --record and I use Pulse audio to select the appropriate source. 

I have tested default source and /dev/dsp but nothing works.


I get with : 
dmesg | grep Mic
[   15.934523] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12  
 
My webcam is named laptop integrated webcam 2M.

Any leads is welcome :)

Thanks for the help

Arnaud

---


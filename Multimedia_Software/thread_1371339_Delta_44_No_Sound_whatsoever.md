---
title: "Delta 44 No Sound whatsoever"
date: 2010-01-03
forum: Multimedia Software
---

### Post by browningjp on 2010-01-03
Hi there,

I am unable to hear any sound at all using my M-audio delta 44 soundcard (which works fine in Windows - Dual boot). I am a complete beginner to Ubuntu and Linux so please can someone explain thoroughly how I can get this working?:confused:

Many Thanks

---

### Post by ajgreeny on 2010-01-03
First check that all your sound levels are right by clicking the volume icon on the desktop panel, and if that looks OK run ```
alsamixer
``` in applications->accessories->terminal where you will see a lot more items you can raise. Play around with that and you may get sound as you want.

If still no luck report back the output of ```
sudo lshw -C multimedia
``` again in terminal, which will show exactly what card you have and the chip used in it.

---

### Post by browningjp on 2010-01-03
I did the alsamixer thing you said: the DAC and DAC 1 were both at 80 and the rest were on 0. I don't know how to change these; when i try to drag them like a mixer, it just highlights the lines.

Here is the output for the sudo lshw -C multimedia command:

jonny@jonny-desktop:~$ sudo lshw -C multimedia
[sudo] password for jonny: 
  *-multimedia            
       description: Multimedia audio controller
       product: ICE1712 [Envy24] PCI Multi-Channel I/O Controller
       vendor: VIA Technologies Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ICE1712 latency=64
       resources: irq:17 ioport:dee0(size=32) ioport:dec0(size=16) ioport:ded0(size=16) ioport:df00(size=64)

---

### Post by ajgreeny on 2010-01-03
I should have said, but in alsamixer:-

1.  move from bar to bar with the left/right cursor keys and 
2.  to raise and lower them use the up/down cursor keys.  
3.  You can use the "M" key to mute and unmute any of them,
4.  tab to go from "playback" to "record" to all" grouped sliders. 
5.  Esc will close it.

---

### Post by browningjp on 2010-01-03
right, I've now figured out how to adjust the controls in alsamixer, but I still have no sound after turning all the channels up.

---


---
title: "Audio Problems with Ubuntu on PepperPad 3"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Pypasaur on 2007-06-03
Just installed Ubuntu Feisty on the PepperPad3 ( [http://www.pepper.com/](http://www.pepper.com/) ).

Unfortunately, the PepperPad3's audio hardware isn't working on Feisty.

Here's what lspci -v says about the audio device inside: 

00:0f.3 Multimedia audio controller: Advanced Micro Devices [AMD] CS5536 [Geode companion] Audio (rev 01)
        Subsystem: Advanced Micro Devices [AMD] CS5536 [Geode companion] Audio
        Flags: 66MHz, medium devsel, IRQ 11
        I/O ports at df80 [size=128]


Feisty automatically loaded module  snd_cs5535audio  during bootup, but  that module isn't working.
Applications can't see the audio device, either.  Alsamixer says:  snd_ctl_open failed for default: No such device

Please help... Thanks in Advance!

---


---
title: "Yamaha YPG-235 midi drivers"
date: 2011-01-20
forum: Multimedia Software
---

### Post by benson1976 on 2011-01-20
Hey all, I am new to Ubuntu, fully installed for a bit over a week now. I am trying to find out how I would install the midi drivers for my Yamaha YPG-235 keyboard. I want to be able to use it in Ubuntu with LMMS and possibly other programs that I don't know about yet. I know that Yamaha (at least Yamaha America) does not offer driver support for any Linux installations. I know it is possible I might get it from one of their foreign distributors (got my canon printers drivers from Canon/New Zealand). Or maybe some knows of another way? Please help, this is the only thing that MIGHT drive me back to windows, but I really do not want that. Any help or suggestions would be appreciated folks. Thanks.

---

### Post by BicyclerBoy on 2011-01-20
The midi support in Linux is in the alsa kernel modules.

AFAIK The printer driver was a mostly a user-space application.
IMO Canon are very good with linux support.

[http://www.faqs.org/docs/Linux-HOWTO/MIDI-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/MIDI-HOWTO.html)

So plug it in and run from terminal
lsmod 
search for midi driver e.g. mad16

If it is USB then run
lsusb
to discover the device ids & name.

Post your output if you like ?

---

### Post by benson1976 on 2011-01-20
Thanks Bicyclerboy, will give it a shot.

---

### Post by benson1976 on 2011-01-20
Thanks Bicyclerboy, will give it a shot.

---


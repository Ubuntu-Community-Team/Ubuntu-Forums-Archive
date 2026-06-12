---
title: "rhythmbox cd extract very slow"
date: 2009-12-21
forum: Multimedia Software
---

### Post by bode on 2009-12-21
no matter what cd ripper i try, rhythmbox, sound juicer, ripperx, etc. the cd reading is extremely slow (3.0x). why is it not operating at full speed and what can i do to fix it? i am using 9.10, cd/dvdrw is connected by sata with the sata power connector converted to 4 pin.

---

### Post by Geremia on 2011-04-07
Running [FONT=Courier New]top[/FONT], I noticed Rhythmbox only uses ~¼ of my CPU. I wonder why.

Also, running [FONT=Courier New]gnome-system-monitor[/FONT], I noticed that Rhythmbox is sleeping even while encoding! [FONT=Courier New]renice[/FONT]-ing it didn't appear to help either.

---

### Post by matt-fender on 2011-04-07
Could do with some more information regarding hardware, what cpu, memory and model of cd/rw drive. Also what quality you are ripping music at, e.g mp3?

---

### Post by Geremia on 2011-04-07
> **matt-fender said:**
> Could do with some more information regarding hardware, what cpu, memory and model of cd/rw drive. Also what quality you are ripping music at, e.g mp3?I have a Macbook 2,1 with 1.25 GB of RAM and a 2 GHz processor. The CD drive is the internal Matshita, and I am ripping to m4a (AAC). Thanks

---

### Post by El Zoido on 2011-04-17
I have the same problem whith Rhythmbox in 10.10 64bit.
Using BonkEnc (free:ac nowadays) under Win7 64bit is insanely fast (3-5 min per cd) at comparable or better quality, it's not hardware.

I switched to SoundJuicer which is somewhat faster, but still not at BonkEnc levels.
System monitor says that I'm only using one of four CPUs and this one not even at full capacity...

---


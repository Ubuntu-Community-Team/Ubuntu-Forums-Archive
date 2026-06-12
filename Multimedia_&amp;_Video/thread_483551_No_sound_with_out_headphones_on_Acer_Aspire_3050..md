---
title: "No sound with out headphones on Acer Aspire 3050."
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by A.P. on 2007-06-24
The sound works just fine with head phones. Doesn't work at all if there's nothing in the head phone jack. Like it thinks there is always something plugged in... I've heard of a possible way to fix this is by typing "acpi=off" in the command line brought up by pressing F6 while booting the Live CD. I've tried this but I think I'm adding it in the wrong place.  Can anyone help?

---

### Post by Gremlinzzz on 2007-06-24
Did ya look at the sound fixs in the ubuntu guide1.14.11sound
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by A.P. on 2007-06-24
Sorry wasn't aware of such a thing. I'll have a look thanks.

EDIT: 

Is this what I should be paying attention to?

Edit the file /etc/modprobe.d/alsa-base: 
gksudo gedit /etc/modprobe.d/alsa-base
Add the following line to the end of the file, replacing '3stack' with your flavor (see below) 
options snd-hda-intel model=3stack

---


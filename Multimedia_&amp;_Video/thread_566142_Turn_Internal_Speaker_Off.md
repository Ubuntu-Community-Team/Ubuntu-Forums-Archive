---
title: "Turn Internal Speaker Off"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by mikeym on 2007-10-03
How can I tell Ubuntu to stop using the Internal Speaker to beep at me?

I've just upgraded and I've found that there is no option in my BIOS to turn of the internal speaker, and I've found that it's incredibly noisy (and I wouldn't realy want to turn it off just to get Ubuntu to stop beeping at me). 

Some of the things that annoy me:

Beep - when doing something it doesn't like tike tabing in the terminal when there're no results.

Beep...Beep...Beep...Beep, Beep, BeepBeepBeepBeep when using 'shutdown' to turn off my computer after watching something as I'm going to bed.

---

### Post by 5-HT on 2007-10-03
i. For the system beep in Gnome:
  Sys -> Prefs -> Sound -> System Beep -> uncheck enable system beep

ii. For the beeps occuring in a terminal:
Blalcklisting the the module responsible so it won't load on boot will do the trick:
echo 'blacklist pcspkr' | sudo tee -a /etc/modules

To unload the running module prior to a reboot:
sudo modprobe -r pcspkr

cheers,

---


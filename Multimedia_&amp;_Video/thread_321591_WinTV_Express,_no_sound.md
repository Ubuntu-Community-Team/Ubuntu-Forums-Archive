---
title: "WinTV Express, no sound"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-19
OK, this is an old chestnut, but how do I get soudn out of my WinTV card? It's a bt878 chip, recognised in dmesg as card 10 and tuner 13. The picture is fine, but there is only a violent humming coming frome the line-out jack (I'll mess with the line-in settings whenever I get sound directly out of it).

In this case, is it that the tuner is badly recognised or there are sound drivers missing for the card? 

Has anyone got this kind of PCI card and knows how to get audio from it?

---

### Post by pickarooney on 2006-12-21
Finally got it, by typing 

sudo rmmod tda9887
sudo modprobe tda9887 port1=1 port2=0 !

I need to add this to some modules file I reckon, but don't know where exactly.
Any ideas?

---


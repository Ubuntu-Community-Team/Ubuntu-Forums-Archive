---
title: "partial lock - sometimes - on one DVB-T network"
date: 2009-01-21
forum: Mythbuntu
---

### Post by dibuntux on 2009-01-21
I really cannot trace this out. I can lock to all networks but one, RAI (national gov. tv in Italy).

Sometimes it works, sometimes it does not. I tried with an amplifier, and signal passed from 61% to 64%, but it is not dependent on % signal; other netowrks work with just 58%.

I get the signal % at 64, partial lock and BE 65535 and the window that tells you "you should have got a signal lock by now..."


using scan, i get a lock on all networks, which BTW are transmitted from a repeater in the same location, but on the RAI networks I get 

Warning: filter timeout pid 0x0011

Other days, it just works. I tried with longer timeouts, but it is the same.

Any suggestions?

My system: Mythbuntu 8.10
Athlon 1700+ 512MB SDRAM PC133
Nvidia 5200 256 MB
Hauppauge HVR 1110 DV-T
SkyStar 2.6 DVB-S

---

### Post by dibuntux on 2009-03-05
OK, I solved this one too the hard way: a fresh install (8.10) cure it. Everything seems the same, but the infamous RAI MUX is now locking. What is strange indeed is the very high bit error compared to other channel with the same % signal strenght: always in the 30000-40000 range compared to 0-100 of other channels, where signal is 62-64% vs. 61-62%. 
As long as it locks and displays fine...

---

### Post by dibuntux on 2009-03-13
Again, it does not work - partial lock & BE 65535 !

Please, anyone has some suggestions, this is really untraceable - somedays it works, some it does not.

It is the same on 9.04 alpha 6.1

---


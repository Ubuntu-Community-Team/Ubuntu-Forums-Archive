---
title: "Suddenly need to activate wireless with fn key!"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by dpatel on 2009-12-02
Hi -

I'm using Ubuntu 9.04. Did a bunch of updates and it seems the function key combo to activate the wireless card (Fn + F7) is required everytime I login or resume from a boot.

Is there a way to force the wireless up without need for Fn + F7?

---

### Post by dpatel on 2009-12-03
I thought I'd give an update since it may help others! I'm still not sure what I did for the issue to occur but here's what solved it:

(For info, I have a Ralink RT2860 card. Also, the Fn + F7 was not consistent - i.e. did not work every time in Ubuntu).

I booted into Windows Vista (dual boot). Had to press Fn + F7 there too but card did work. Then put laptop into standby followed by resume. Now, wireless card did NOT activate - had to press Fn + F7 again. However, this time I only had limited connectivity. To get full connectivity I had to disconnect->reconnect.

Went through above process a couple of times to be sure it was consistent. Then rang Medion (manufacturer) as laptop was still in warranty. They stated I needed to do a factory reset (using recovery CD) to be sure it was a hardware issue before I could send laptop for repair.

I did the factory reset - amazingly it did not remove my Ubuntu partitions. Anyway, after reset the wireless card worked fine in Vista even after standby. Then booted into Ubuntu (did not change anything here) and it was working again!

How bizarre is that?! I can only guess that the drivers that were reloaded as part of the factory reset also write something to the Ralink card. Can anyone confirm that is the case?

---


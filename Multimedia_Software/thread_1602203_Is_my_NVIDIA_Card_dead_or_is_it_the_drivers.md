---
title: "Is my NVIDIA Card dead or is it the drivers?"
date: 2010-10-21
forum: Multimedia Software
---

### Post by mattmarq on 2010-10-21
I am not sure if this is the right forum category for this thread, but bear with me.

I use my BFG GTX 280 OC video card for both Ubuntu 10.10 and for Windows XP. For a few months on XP, it has crashed when running any 3d accelerated video game. It also crashes when view websites with flash videos aka youtube. 

The screen goes multicolor with lines everywhere similar to the effect of removing a cartridge from an NES while it is on, or the screen goes a solid color. Either way, the computer locks up, and I must restart.

The same issue is happening in Ubuntu 10.10 when I view youtube. A complete lock-up of the screen happens, and I have to restart.

I have uninstalled the proprietary NVIDIA drivers in Ubuntu, and now, I can view youtube without an issue. 

Am I using my NVIDIA graphics card when I do not have the drivers installed in Ubuntu? My intuition is that it is not being used and my card is dead, but I am not sure if there is an open driver that is used when I removed the proprietary driver. Although, I have had an ATI card before, and maybe I am getting confused.

I am trying to determine if this card is completely dead as BFG does not provide RMA anymore, and PNY is only offering their discount for BFG customers with dead cards for another 10 days.

Any help is greatly appreciated!

---

### Post by mattmarq on 2010-10-21
Well, after viewing a few more videos on youtube,the computer locked up again. This leads me to believe the card is being used and is in fact, dead.

Although, I am still interested in hearing if anyone knows for sure if the NVIDIA card is being used when the proprietary driver is not installed.

Thanks again.

---

### Post by cascade9 on 2010-10-21
If your video is coming from the nvidia card, its in use, no matter if youur using the nvidia drivers, or any of the free drivers. 

Hmm, is 10.10 still using beta drivers? That could be causing problems as well.... 

"The screen goes multicolor with lines everywhere"? That sounds like your card is cooked in some way. You can try 2 things- take the side of your case, point a nice, big desktop fan into the case, turn it on then boot the computer (the extra airflow should stop the card from overheating, if thats causing the issue). Or you can get nvclock, and underclock the heck out of it.

---

### Post by mattmarq on 2010-10-21
Well, I woke up this morning, and now the computer is booting right into terminal.
 
Even if my card is dead, shouldn't I still see a very simple GUI when booting into Ubuntu? 

Thanks for the suggestions cascade9. I do not think overheating is an issue as the card seems more prone to work when left to heat up for a while. I've seen a few suggestions to actually put my card in the oven to resolder it (too crazy a solution for me).

---

### Post by soldier1st on 2010-10-21
could you test your video card in another system?

---

### Post by mattmarq on 2010-10-21
Unfortunately, I do not have another system to try it in. Worse comes to worst, I buy a new card and have two working cards with the same problem. 

:guitar:

All the hardware forums have insisted it is my card. The bizarre visual lock-up of the screen is not likely caused by anything else.

---

### Post by inobe on 2010-10-21
> **mattmarq said:**
> Well, I woke up this morning, and now the computer is booting right into terminal.
 
Even if my card is dead, shouldn't I still see a very simple GUI when booting into Ubuntu? 

Thanks for the suggestions cascade9. I do not think overheating is an issue as the card seems more prone to work when left to heat up for a while. I've seen a few suggestions to actually put my card in the oven to resolder it (too crazy a solution for me).

have you reseated this card, back when i had a bfg 6800gt that did this and the fix was removing it and putting it back, i guess it had bad contact.

---


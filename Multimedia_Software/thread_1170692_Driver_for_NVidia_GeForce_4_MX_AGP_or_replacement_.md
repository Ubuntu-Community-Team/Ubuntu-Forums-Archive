---
title: "Driver for NVidia GeForce 4 MX AGP or replacement card?"
date: 2009-05-26
forum: Multimedia Software
---

### Post by ChuckV on 2009-05-26
I'm running an older Dell Dimension 4100 with an NVidia GeForce 4 MX AGP card.  The NVidia driver does not work correctly - it doesn't get my monitor properties correctly, misdraws some window title bars, doesn't allow window dragging and some other window operations.  This is the case for both the proprietary driver packaged with Ubuntu and the one downloaded from NVidia itself.

The free driver for this old card is slow.  Video performance is significantly poorer than windows.  Of course, being correct and slow is better than fast and wrong.

So, I'm thinking about a new card.  What cards would work well - i.e. have good performance ubuntu drivers (either free or restricted)?

My system (yes, it's old):
Dell dimension 4100
Pentium 3 933 MHz.
512 MB ram
500 GB drive
AGP slot
Monitor has both digital and analog connection, digital preferrred.

---

### Post by pro003 on 2009-05-26
The way to go is envyng. Install it from terminal:

```
sudo aptitude update
sudo aptitude install envyng-qt envyng-core envyng-gtk
```

launch it and it will select the best recommended driver. Usually always works for nvidia cards.

---

### Post by ChuckV on 2009-05-26
Thanks, but that didn't work.

EnvyNG gave two options:
96.43.10, which I have tried previously
71.86.08, which did not work at all.

:(

I'm back to looking for a card.

---

### Post by pro003 on 2009-05-26
sorry to hear that. suit yourself...

---


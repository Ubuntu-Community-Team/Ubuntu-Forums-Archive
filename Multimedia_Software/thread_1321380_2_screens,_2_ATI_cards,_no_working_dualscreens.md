---
title: "2 screens, 2 ATI cards, no working dualscreens"
date: 2009-11-10
forum: Multimedia Software
---

### Post by brigzzy on 2009-11-10
Hello all, I'm running 2 ATI Radeon hd 4870s, connected with a crossfire bridge, but I can't get dual displays working.  I've seen lots of posts with guides for configuring two displays on one card, but my setup has two cards, with each monitor plugged into it's own card.  I'm running the drivers from the ATI (Or I guess I should say AMD) site, but the catalyst control center won't acknowledge the second card.  I'm hoping someone out there can help me with my problem.

Thanks in advance
Brigzzy

---

### Post by markbuntu on 2009-11-10
The second card should appear in the catalyst control center/display manager in the box beneath the display, you can drag it into the display area and the second display should now be shown. 

Which driver from ati, is it the latest 9.10 or an earlier one?

You can also look in the Xorg.0.log to see if both cards are detected.

Anyway, if you do not get the card figured out in CCC you can try this from a terminal.

sudo aticonfig --adapters=all -initial -f

btw crossfire is for only one monitor on two cards so make sure that you do not have crossfire enabled but you probably know that already 

aticonfig --help

for more help.

---


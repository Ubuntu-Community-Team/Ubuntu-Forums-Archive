---
title: "Garbled Graphics on Radeon 7500"
date: 2005-12-30
forum: Multimedia &amp; Video
---

### Post by prarie on 2005-12-30
I recently changed the motherboard after the old one died. The new motherboard is an MSI KM4M-V (Via KM400 + 8237). 

Ubuntu installed and worked fine on the old motherboard when I was playing with it. Windows XP works fine now - but I want to switch my system to Ubuntu.

The display of Ubuntu on the new motherboard is completely screwy.

There is a square where the mouse pointer is that changes the colour of whatever I move the pointer over. Once logged in the background is completely garbled and widgets are only readable when the mouse is hovered over them. Normal text isn't readable at all.

In addition to the motherboard mentioned above I have the following:

AMD 1800+
ATI Radeon 7500
New 300GB SATA drive I'm installing onto

I have tried messing with pkg-reconfigure for xserve but with no luck - choosing vesa causes X to freeze while loading before login.
 
Hope someone can help,
Thanks

---

### Post by DoorGunner on 2005-12-30
What i think has happened is since your mother board has changed fglrx may need to be re-configed in order for it to recognize the new change. I could be wrong.

Have you tried doing a fglrxconfig ? or remove and reinstall your drivers?

---

### Post by prarie on 2005-12-30
[QUOTE=DoorGunner]Have you tried doing a fglrxconfig ? or remove and reinstall your drivers?[/QUOTE]

No, but I don't think I have the fglrx drivers installed. fglrxconfig at the command prompt isn't found.

My understanding is those drivers are not needed for the radeon 7500 since it's supported by the X ati drivers. This is shown here [http://www.ati.com/developer/altoschart.pdf](http://www.ati.com/developer/altoschart.pdf)

Mind you, I am quite new at this and could be quite wrong.

---

### Post by prarie on 2005-12-30
Also, this is a new installation of Ubuntu so it would have recognized the new motherboard already.

---

### Post by qb4ever on 2006-01-03
Give the VGA driver a test.

---


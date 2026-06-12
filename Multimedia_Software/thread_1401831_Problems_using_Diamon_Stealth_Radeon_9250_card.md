---
title: "Problems using Diamon Stealth Radeon 9250 card"
date: 2010-02-08
forum: Multimedia Software
---

### Post by faldrich on 2010-02-08
This all began when I first installed Ubuntu 9.10 on an IBM x3200 server -- the system would boot into Ubuntu, I'd see the logo, then it would reboot itself. When I took out the card, all was fine.

Long story short, there seems to be a driver issue.

I was also having trouble running the ElectricSheep screen saver (a must have, for me).

When I installed the fglrx driver, pointing ElectricSheep to the "gl" driver, it works. But, Ubuntu won't enable the desktop effects, and I know this card is perfectly capable of all of that.

I saw a web page that talks about removing the fglrx driver and doing some other configuration -- it looks overly complicated, and it seems like Ubuntu should do the right thing--- ?

I wonder if someone could lend a hand to help diagnose and figure this one out?

In order to get a full-screen display of the ElectricSheep screen saver, I must point it to the "xv" driver (via electricsheep-preferences). Otherwise, it ends up being a small square.

Thank you in advance....

---


---
title: "nVidia vs ATI multi display support?"
date: 2010-03-07
forum: Multimedia Software
---

### Post by aj7360 on 2010-03-07
I have been running 3 monitors with 2 nVidia cards for some time now. Last week one of the nVidia cards died. 

As I have more "old" ATI cards laying around (which I prefer for gaming on my XP box) I thought I would try a similar setup using ATI cards. 

So I uninstalled the nVidia driver, swapped out the cards and put in the first ATI card, a Radeon X800XL.(AGP) Started up Ubuntu 9.10 (64) and started the Hardware Drivers process, which found nothing. (For my nVidia 5900 it found three drivers). 

Okay... guess it's **too** old. So I installed a much newer PCI-e HD4350 tried again and it did find a driver. I then reinstalled the X800. (Mobd) has both PCI-e and AGP slots and went into the CCC to set the displays.

I use three separate X-displays since my monitors are different sizes. I used the machine for teleworking where my job mostly involves unix shell scripting.

The ATI driver doesn't even seem to have that option! What the heck? 

I thought of manually editing the xorg.conf but with three heads and 2 cards I was pretty sure that would take me hours to get that to work and it was just easier to go back to the nVidia cards. 

The question is does the ATI drivers support separate X displays?? Should I have tried to download and install vid drivers from ATI instead of the Ubuntu software center?

And if so, would it support the use of onboard video AND PCI-e at the same time to run separate x-displays? Newegg has very few AMD boards with onboard video AND multiple PCI-e slots, which would give me maximum flexibility in the future.

---


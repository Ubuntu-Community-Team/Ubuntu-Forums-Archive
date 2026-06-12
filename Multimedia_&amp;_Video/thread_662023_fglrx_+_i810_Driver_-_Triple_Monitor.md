---
title: "fglrx + i810 Driver - Triple Monitor?"
date: 2008-01-08
forum: Multimedia &amp; Video
---

### Post by sleizure on 2008-01-08
I have a system with onboard video using the I810 intel driver (It is a GMA X3000), and an ATI Radeon 2400. I am hoping to use this for Triple Monitor Purposes. I can install fglrx from the ATI site without issues and configure xorg.conf to supply dual displays through the ATI card, however unable to get it to work with the i810 driver and fglrx concurrently. Has ATI limited this ability from loading any other video drivers?

---

### Post by sleizure on 2008-01-14
Update: I've tried the gutsy xorg official drivers and still no go. The intel card just seems to make everything stop. 

Anyone?

---

### Post by patrickfromspain on 2008-01-14
You won't be able to have triple monitor with 2 different graphic cards: it's impossible. Impossible in linux and impossible in windows.

For three displays you would need a graphic card with 2 DVI outputs, since on a DVI output you can attach a sort of Y on which you can attach 2 screens (not sure if they can display different stuff or they would show the same, use google for more info).

To use 2 graphic card at the same time you must have an NVIDIA SLI or an Ati Crossfire array of cards.. which means you need a motherboard with 2 pci express slots and 2 identical sli capable cards (for nvidia) or an ati crossfire capable card and its crossfire unit (case of ati)

---

### Post by sleizure on 2008-01-14
Thanks for your response. 
I understand that in Vista using the new WDDM device driver model you are unable to utilize the latest Aero interface, did not think that Linux suffered the same fate. For what its worth I am on a Windows XP machine right now and using 3 monitors with the ATI Radeon HD2400 and Intel X3000 onboard graphics without issues. Really wanted to make the switch but I guess its just not in the cards.

---

### Post by patrickfromspain on 2008-01-15
oh sorry man, I though it wasn't possible. This may help:

[http://ubuntuforums.org/showthread.php?t=550629&highlight=triple+monitor](http://ubuntuforums.org/showthread.php?t=550629&highlight=triple+monitor)

---


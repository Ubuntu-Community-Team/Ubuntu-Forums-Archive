---
title: "One ethernet card gone missing"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by Mastodront on 2006-01-09
Now I've got a quite weird problem;
All of a sudden one of my ethernet cards just went missing. I have two cards, one integrated in the motherboard (using it for my internet connection) and one PCI (using it to connect to my xbox) which is the one that disappeared.

I have never had any problems earlier, both Warty, Hoary and Breezy have found the card automatically but by some reason it's just gone now :/

If I start network-admin I can see "Ethernet connection - The interface eth0 is active" and modem connection but not the other card that always used to be there. 

The only thing I know has happened lately is that I've cleared the CMOS a couple of times because of some hardware problems but when I checked the BIOS settings I could find nothing wrong. Anyone who has any tips?

---

### Post by vruum on 2006-01-09
do you know what kind of card it is? do you have a live cd lying around somewhere, if so, try booting it up and see if it detects the card, alternative boot up with the ubuntu install cd, and walk through the steps until you reach the network detection, of course don't install partition or delete anything, just to make sure it is not a bios/cmos issue. If the second card is detected, take note of what kind of card it claims to be, and figure out the driver it needs, then boot up in ubuntu, and 
> sudo modprobe $DRIVER

---

### Post by Mastodront on 2006-01-10
Thanks for the tips :)

I tried booting my Breezy Live-CD (which always used to find my card) but it couldn't find it anymore. :/
I guess it's either broken or that something happened during the CMOS clearing...

---

### Post by az on 2006-01-10
If it is an isa card, you may have a ressource conflict - the irq may be assigned to another piece of hardware.  You need to assign this by hand in your CMOS (Bios)

---


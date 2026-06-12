---
title: "Blank Screen ocassionally"
date: 2015-04-24
forum: Mythbuntu
---

### Post by ODBWilson on 2015-04-24
Mythbuntu 12.04.3

I have already disabled screen saver, "Lock Screen", and power management.

xset q
====
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0

DPMS (Energy Star):
  Standby: 7200    Suspend: 7200    Off: 14400
  DPMS is Disabled

But ocassionally, the screen is still blank.  It happens randomly.
I can use mouse or keyboard to turn on the screen.
However, sometimes it might just shows a cursor on the left upper corner; it can't get back to the desktop.  

Any clues to completely stop the blink screen.  Any other settings I forgot?

Cheers/Wilson

---

### Post by ODBWilson on 2015-04-27
Any clues?

---

### Post by QDR06VV9 on 2015-04-27
[Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ubuntu/ppa") Took care of that for me!

```
sudo apt-add-repository ppa:caffeine-developers/ppa
```
Update the local repos:```
sudo apt-get update
```
Install Caffeine:
```
sudo apt-get install caffeine
```
Then look in your menu for the app click on it, done.
Regards

---

### Post by Frogs Hair on 2015-04-27
*Moved to **Mythbuntu ***

---


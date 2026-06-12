---
title: "Natty boots to a black screen"
date: 2011-02-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-02-06
It seems my Natty install boots to a black screen where my monitor just goes into power saving as it seems there is no output.

I am guessing I must have some missing packages?

---

### Post by nowin4me on 2011-02-06
You probably need to install graphic drivers. Are you dual booting? I have the same problem at the moment, grub is completely black as if there is no input.

For me at least I found out if I press the arrow key down 4 times ill boot up windows 7, if I want to go onto ubuntu I have to either wait or press the enter key. While ubuntu is loading up the screen is completely black still.

---

### Post by ubername on 2011-02-06
Is it the grub menu which is black, or, as I suspect, once you have selected Natty from the grub menu?

If the latter, try selecting the recovery option from your grub menu, and then select the 'dpkg - fix broken packages' option (I can't remember the exact name off the top of my head)

When that has finished, try the Failsafe graphics mode. Somewhere along the way these steps may help.

N.B - if you have an Nvidia graphics card things are a bit unstable at the moment. If you manage to get to a GUI try running the 'additional drivers' option from System>Administration and playing with that. I am currently getting best results with no additional drivers and foregoing any desktop effects, but you may have other results / preferences.

---

### Post by ELD on 2011-02-06
It's after i select to boot Natty, recovery mode tried and the failsafe graphics mode also goes to black screen.

Re-installing from alpha 2 cd to see if it works.

---


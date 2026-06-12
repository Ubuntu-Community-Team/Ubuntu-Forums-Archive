---
title: "videos have lines when panning."
date: 2009-02-22
forum: Multimedia Software
---

### Post by terry_gardener on 2009-02-22
hello, please can someone help. 

i seem to have a problem with videos, when video picture is panning left to right or up and down it is giving lines across the screen. i have checked and it works alot smoother when desktop effects is switched off. 

i mainly use vlc as my main media player.seems to happen in intrepid and jaunty. 

i have tried the following things. 
changing the video output from xvideo to x11 in vlc 
also tried this using gstreamer-properties

is there anything that i can do to get this to work with desktop effects turned on. 

i have also attached the xorg.conf file if it helps.

---

### Post by terry_gardener on 2009-02-22
i think i might have solved it, by ticking the sync to vblank in compiz settings manager.

---

### Post by Dawei87 on 2009-02-24
what do you mean by sync to vblank? i am having the same problem as well

---

### Post by terry_gardener on 2009-02-25
Dawei87

i opened the compiz settings manager (system-preferences-compiz setting manager). 
click general options and then display settings tab. 
tick the sync to vblank option (think it is the bottom option) 

hope this helps. 

i have tested since and it did solve my problem.

---

### Post by Dawei87 on 2009-02-26
thanks so much!! im gonna keep testing for nor but im pretty sure it did it!!

EDIT: ugh. well it didnt fix the lines on the screen, but it did seems to reduce them. im not for sure, but i thought it was fixed for a minute.

---

### Post by terry_gardener on 2009-02-26
what gpu do you have.

---

### Post by Dawei87 on 2009-02-26
ati radeon hd 3200

---

### Post by terry_gardener on 2009-02-27
Dawei87

sorry but i have a nvidia 7900gs. 

might be worth looking in the ati setting manager if it has one for sync to vblank and ticking the options. 

sorry i cant help anymore but never used ati with ubuntu before.

---


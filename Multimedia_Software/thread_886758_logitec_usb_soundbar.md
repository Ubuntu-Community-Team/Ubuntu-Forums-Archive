---
title: "logitec usb soundbar"
date: 2008-08-11
forum: Multimedia Software
---

### Post by Trmptxn on 2008-08-11
a few weeks ago, i bought a logitec usb soundbar. i quikly ran into a problem however.  if i boot with the speakers plugged in ill get sound out of it, but the sound will be accompanied by a loud clicking noise.  if i just plug it in while the computers already running it will either not be detected, or the clicking noise will start again and the Ubuntu startup noise will play.  i do want to get this working rather badly because i need some external speakers to play music on.  if anyone can point me in the right direction it would be apreciated. i am currently running ubuntu 8.04, with all the latest updates.  i am running it on a dell inspiron e1505 laptop.  

many wins to any who can help me!

---

### Post by wolfen69 on 2008-08-11
right click your speaker icon and go to "open volume control". see if any of the settings in there will change something.

---

### Post by Trmptxn on 2008-08-11
nada, when i boot up with it plugged it, it shows up under the system-preferences-sound menu as "usb audio" but when i plug it in with the computer running, it will say "usb audio not detected"

---

### Post by Trmptxn on 2008-08-19
cool, i got one half of the problem down =) 

by using the command asoundconf set-default-card Speaker i can plug in the speakers and they will work just as soon as i run that command =) i got that half of the solution from this thread  [http://ubuntuforums.org/showthread.php?t=903863&highlight=usb+sound&page=2](http://ubuntuforums.org/showthread.php?t=903863&highlight=usb+sound&page=2)  

i still have the problem with a buzzing noise coming from the speakers when audio is playing though

---

### Post by erikthedrink on 2009-09-08
Press the volume icon, choose Select Controls, Select PCM.  Turning the PCM switch down from full (all the way up) gain should make the static hiss disappear.:P

---


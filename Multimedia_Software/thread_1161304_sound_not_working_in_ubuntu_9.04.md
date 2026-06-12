---
title: "sound not working in ubuntu 9.04"
date: 2009-05-16
forum: Multimedia Software
---

### Post by maboli on 2009-05-16
i installed ubuntu 9.04 without any problems even for the sound then i had a problem and i had to re install it again since then the sound didnt work i tried almost every thing .... plz help

---

### Post by Teutorix on 2009-05-16
So the sound is broken from re-installing if im reading that correctly?

---

### Post by maboli on 2009-05-16
thats what i think it it is ...

---

### Post by Teutorix on 2009-05-16
type
```
alsamixer
```
into the terminal and check that the master volume is up

---

### Post by raymondh on 2009-05-16
> **Teutorix said:**
> 
into the terminal and check that the master volume is up

or that nothing is muted.

Good luck

---

### Post by maboli on 2009-05-16
ive tried that before , and ive checked now nothing is muted and there is no sound !!!

---

### Post by Teutorix on 2009-05-16
do you know what kind of soundcard you have, if so manually install the drivers from the manufacturer's site and restart your computer, that worked for my intrepid sound issues

---

### Post by maboli on 2009-05-16
but the last time (i installed ubuntu) it worked by it self !!!

---

### Post by raymondh on 2009-05-16
> **maboli said:**
> but the last time (i installed ubuntu) it worked by it self !!!

Maybe on the reinstall the drivers did not load.  Have you updated your drivers since the re-install?  Try system > administrative > hardware drivers.

---

### Post by maboli on 2009-05-17
> **raymondhenson said:**
> Maybe on the reinstall the drivers did not load.  Have you updated your drivers since the re-install?  Try system > administrative > hardware drivers.
i did the update from the update manager .
when i open the HARDWARE DRIVERS i get "no proprietari drivers are in use on this system" ...
what should i do ?

---

### Post by raymondh on 2009-05-18
Hello Maboli,


When you re-installed, did you also load/install ubuntu-restricted-extras?  Just asking, because they have the codecs.  If not, go to synaptics and search/install from there.  Then reboot.

Also, here's some HOW TO's from the forum.  Hope these can help you.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

Good luck,

---

### Post by maboli on 2009-05-18
thank you so much

---

### Post by raymondh on 2009-05-19
> **maboli said:**
> thank you so much

fixed?

---

### Post by maboli on 2009-05-19
> **raymondhenson said:**
> fixed?
no not yet , 
the likns you gave me are very hard to follow , i decided to isntall ubuntu 8.10 then if the sound works ill upgrade ...

---


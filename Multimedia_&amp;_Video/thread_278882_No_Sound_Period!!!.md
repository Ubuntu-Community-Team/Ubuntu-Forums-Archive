---
title: "No Sound Period!!!"
date: 2006-10-17
forum: Multimedia &amp; Video
---

### Post by rohan076 on 2006-10-17
OK guys I've tried everything!!! even the comprehensive guide! but to no avail! help will be appreciated. I am running ubuntu on a sony vaio laptop

---

### Post by ciscosurfer on 2006-10-17
I don't know to which guide you are referring.  So you've made sure that you are setup to use the correct Audio card, correct?  Under the Sound admin panel?

---

### Post by Kateikyoushi on 2006-10-17
I also have a vaio laptop and the soundcard was detected and set up automatically but had to play with the alsamixer settings.
Had to mute the external amlifier otherwise had no sound.

---

### Post by PugTheBlack on 2006-10-17
Hehe Im having the NO SOUND PERIOD!! Problem too ;) 

Im running Ubuntu 6.06 on an Elitegroup 910 Laptop, and to be honest Im not sure the chipset it supported in ALSA yet so I got it reported as a bug there...

You could try posting a bugreport too and see if they can help you out. Are you running the latest ALSA drivers btw? ( 1.0.13 ) 

sudo cat /proc/asound/version 

Oh well - I'll just wait and see what kind of answer I get from the ALSA project, and if they think my chipset SHOULD be supported I will get back to working on it ;-) 

[https://bugtrack.alsa-project.org/alsa-bug/main_page.php](https://bugtrack.alsa-project.org/alsa-bug/main_page.php) - IF you are running the latest alsa drivers and have had no problems with them - report a bug here and see if they can help you out. 

-Pug

---


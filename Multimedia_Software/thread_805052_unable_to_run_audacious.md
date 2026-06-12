---
title: "unable to run audacious"
date: 2008-05-23
forum: Multimedia Software
---

### Post by dingo17 on 2008-05-23
I was trying to make audacious default mp3 player and somehow I managed to make it unable to run.....i have tried to run audacious every possible way but it always runs rhythmbox.....where is problem??

---

### Post by gandaran on 2008-05-23
> **dingo17 said:**
> I was trying to make audacious default mp3 player and somehow I managed to make it unable to run.....i have tried to run audacious every possible way but it always runs rhythmbox.....where is problem??

you must give more details! what exactly you trying to do? if you go to applications » sound and video » audacious, when you click audacious, does it open up or not? or does rhythmbox start?

---

### Post by dingo17 on 2008-05-25
I figured out what was wrong......I was trying to make audacious default mp3 player and I found somewhere that should run this command > sudo ln -s /usr/bin/rhythmbox /usr/local/bin/audacious so I just deleted audacious file in /usr/local/bin/ and it is working again.....but I still can't figure out how to make audacious default mp3 player in gnome commander, every way I have tried worked only for nautilus....can you help me??

---

### Post by gandaran on 2008-05-25
have you tried system » preferences » applications » multimedia tab?
change rhythmbox to a personalized command 'audacious' or '/usr/bin/audacious'

---


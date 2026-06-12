---
title: "Can't play more sounds at same time !"
date: 2008-11-23
forum: Multimedia Software
---

### Post by warzt on 2008-11-23
Help please, I can't hear anything else when playing music. So when i need hear email notification, I must turn off alsa player ( now i am using this ).
I did try 
~$ asoundconf set-default-card < Names of available sound cards >
But i doesn't work :(

---

### Post by zander1013 on 2008-11-23
> **warzt said:**
> Help please, I can't hear anything else when playing music. So when i need hear email notification, I must turn off alsa player ( now i am using this ).
I did try 
~$ asoundconf set-default-card < Names of available sound cards >
But i doesn't work :(


try alsaconf and then if you have not already try installing libesd-alsa0 and gnome-audio.

-zander

---


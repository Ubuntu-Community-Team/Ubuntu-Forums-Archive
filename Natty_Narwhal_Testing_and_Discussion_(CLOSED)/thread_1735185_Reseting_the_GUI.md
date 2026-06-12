---
title: "Reseting the GUI"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2011-04-21
I have just done a fresh install and I kept my Home dir (as you do). But I'm trying to remember what folders I need to delete that will reset the GUI back to default settings just like a fresh install (if thats the correct method, its the way I was tought but now I can't remember which folders it is). I don't want to loose the individual application data though.

---

### Post by dino99 on 2011-04-21
most of the settings are into .gconf (/home, ctrl+h to unhidden)

you can try also (only reconfiguring):

sudo dpkg-reconfigure -phigh -a
( could need some times, dont stop it)

---

### Post by Jonny87 on 2011-04-21
> **dino99 said:**
> most of the settings are into .gconf (/home, ctrl+h to unhidden)

you can try also (only reconfiguring):

sudo dpkg-reconfigure -phigh -a
( could need some times, dont stop it)
I'm guessing that ```
sudo dpkg-reconfigure -phigh -a
``` is safe to run. Will this work the same for both gnome and unity?

---


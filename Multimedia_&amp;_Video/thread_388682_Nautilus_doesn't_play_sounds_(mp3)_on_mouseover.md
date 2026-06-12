---
title: "Nautilus doesn't play sounds (mp3) on mouseover"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by jej2003 on 2007-03-19
I have installed the restricted formats package but do not get sounds from mp3s when I mouse over them.  Is there a way to figure out why?

---

### Post by jpeddicord on 2007-03-20
Open Synaptic from System > Admin > Synaptic, and install the "mpg321" package. Then sign out of your session and then sign in again.

If you are familiar with the terminal, this method is much faster:
```
sudo apt-get install mpg321
killall nautilus
```You do not have to restart after using the terminal method.

Either method should give you sound previews. :)

---

### Post by Cappy on 2007-03-21
Another thing is that you need to use "view as icons" and not "view as list"

---


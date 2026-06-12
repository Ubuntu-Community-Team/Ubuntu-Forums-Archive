---
title: "no sound when i have audio call"
date: 2010-07-09
forum: Multimedia Software
---

### Post by drsawah on 2010-07-09
iam using skype and pidgin(google talk) when i nave audo call there ara no ringing just it show ther is some one call me witout sound
how i can active the ring sound in both app

---

### Post by lidex on 2010-07-09
Check your mixer settings. Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---


---
title: "can not hide controls in Movie player"
date: 2010-03-09
forum: Multimedia Software
---

### Post by ginbuntu on 2010-03-09
I want to hide the controls of Movie player (totem). I can hide it by going to view->show controls. but when I reopen Totem, it shows the controls again. it seems Movie player does not save the settings correctly. 
Any workaround for this?

---

### Post by mc4man on 2010-03-09
Well if you can't find a setting (doesn't appear to be one in gconf) you could do this, it will quickly remove the contols when opening totem

run in a terminal 
```
alacarte
```

highlight Sound & Video and right click on Movie Player -> properties.
Change the default launch command to this 
```
totem --toggle-controls %U
```

Best I can think of atm

---

### Post by ginbuntu on 2010-03-10
thank you. it works great.

---


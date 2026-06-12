---
title: "Qjackctl has no GUI!"
date: 2008-10-26
forum: Multimedia Software
---

### Post by Envergure on 2008-10-26
Qjackctl (the GUI interface for JACK) has no GUI!
[See attachment]
Look closely and you can see lighter spots where buttons should be.

Possible cause:  I installed both K and GNOME and recently (today) i removed K.  Maybe i removed something i shouldn't have.

---

### Post by wolfen69 on 2008-10-26
completely remove qjackctl and then do:
```
sudo apt-get clean
```then
```
sudo apt-get autoremove
```then reinstall qjackctl. it should reinstall any missing dependencies.

---

### Post by Envergure on 2008-10-26
Nope.

---

### Post by Envergure on 2008-10-26
Nope.  But now when i minimize it and maximize it again it looks right :)

---


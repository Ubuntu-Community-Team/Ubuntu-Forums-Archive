---
title: "Cannot enter into a gnome session through GDM"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MishaAct on 2010-10-01
I choose account and enter password, confirm. But enter back into the gdm after that.
# Entered gnome through startx

---

### Post by lidex on 2010-10-02
Try re-installing GDM:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---


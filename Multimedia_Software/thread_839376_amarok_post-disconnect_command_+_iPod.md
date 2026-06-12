---
title: "amarok post-disconnect command + iPod"
date: 2008-06-24
forum: Multimedia Software
---

### Post by Karakh on 2008-06-24
It seems that whatever I use I get:> Post-disconnect command failed, before removing device, please make sure that it is safe to do so.and the ipod does not unmount/eject.

so far I have tried:
```

gnome-eject -e -n -d /media/iPod
gnome-eject %d
eject %d
```and variations upon.

I don't know if it makes a difference, but I'm using Mint 5.0

---

### Post by Karakh on 2008-06-24
OK, I'm getting a kind of half eject with:
```
gnome-eject -t -d %d /dev/sdc2
```
But I still get the error.

---

### Post by aeiah on 2008-06-24
what about umount?

---

### Post by Karakh on 2008-06-24
> **aeiah said:**
> what about umount?

Awesome, thanks alot. Got it to work with```
umount /dev/sdc2
```

---


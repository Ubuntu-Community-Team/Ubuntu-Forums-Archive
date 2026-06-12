---
title: "Viber not working (white window), probably after system update"
date: 2019-02-11
forum: Multimedia Software
---

### Post by qjmann on 2019-02-11
Viber has stopped working - shows only a white screen and it's icon in statusbar. Probably, it happened after recent Ubuntu system update. Tried to reinstall the newest version manually, via dpkg, and there was a compatibility problem "Package libcurl3 is not installed". Fixed it with sudo apt --fix-broken install && sudo apt install libcurl3, then installed viber from the deb file via dpkg successfully. But problem stills here. If trying to launch viber as sudo, the window isn't completely white, but all fonts are broken and completely unreadable.

---

### Post by qjmann on 2019-02-17
Seems like I'm the only one at Ubuntuforums experiencing this terrible issue. I've found the solution on Reddit discussion ("**Viber white screen after latest update**").
Execute this in command line:
```
$ rm -rf ~/.cache/qtshadercache
```

---

### Post by asdfasdf81 on 2019-07-24
Will executing clear cache have any effect in clearing the existing viber history ?

I am having the same issue, and I assume executing the clear cache might do the trick, but I do not want to clear my existing history.

---

### Post by qjmann on 2019-07-25
I don't remember if the history disappeared or not after that - too much time have passed. But I believe, it shouldn't disappear, because it is not a common Viber's cache, but a QT's cache - probably, something related to visual interface, not to the program's data.

---

### Post by asdfasdf81 on 2019-08-03
Thanks a lot. Did save me.

---

### Post by colovrat on 2019-11-01
Hi! Perfect solution. Super Montana !!! Thank You very much. Alex.

---


---
title: "Help! SDL Errors"
date: 2012-02-04
forum: Multimedia Software
---

### Post by Ahmed Shaker on 2012-02-04
I've been trying to install SDL, but I keep on getting this.


make: Nothing to be done for `all'.
/bin/bash build-scripts/mkinstalldirs /usr/local/bin
/usr/bin/install -c -m 755 sdl-config /usr/local/bin/sdl-config
/usr/bin/install: cannot remove `/usr/local/bin/sdl-config': Permission denied
make: *** [install-bin] Error 1


Can anyone help me?:confused:

---

### Post by Rodney9 on 2012-02-04
Try 

sudo make



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by MoreOrLess on 2012-02-04
You do not need to build it. SDL is installable through the repo:
```
sudo apt-get install libsdl1.2-dev
```

---


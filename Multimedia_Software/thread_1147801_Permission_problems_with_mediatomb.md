---
title: "Permission problems with mediatomb"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Sonobana on 2009-05-03
Hi!

Hi i use mediatomb as a daemon. Media-files are at Users home directory. When i try to watch picture for example i get error and on log it read in finnish "Lupa evätty" which means like "access denied". I have tried change permissions:

```

cd ~
sudo chown -R myuser:meditomb Pictures/
sudo chmod -R 755 Pictures/

```

but this dosent seem to help. When i run mediatomb as user it works just fine, at least when all the files are on one users home directory. How i get the daemonmod to work? :confused:](*,)

I'am running Jaunty.

Edit:
- Tried with sudo

---

### Post by fdrake on 2009-05-03
try with sudo first:
```
sudo chown -R myuser:meditomb Pictures/
sudo chmod -R 755 Pictures/
```

---

### Post by Sonobana on 2009-05-04
> **fdrake said:**
> try with sudo first:
```
sudo chown -R myuser:meditomb Pictures/
sudo chmod -R 755 Pictures/
```

Thanks, but that didn't help.

---

### Post by fdrake on 2009-05-04
did u see [this post]("http://ubuntuforums.org/showthread.php?t=890136")?

---

### Post by Sonobana on 2009-05-07
> **fdrake said:**
> did u see [this post]("http://ubuntuforums.org/showthread.php?t=890136")?

Yeah, but i need mediatomb to be system global daemon.

---


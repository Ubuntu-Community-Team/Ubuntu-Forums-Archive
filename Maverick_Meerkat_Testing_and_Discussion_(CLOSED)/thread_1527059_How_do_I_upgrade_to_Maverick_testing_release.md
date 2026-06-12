---
title: "How do I upgrade to Maverick testing release?"
date: 2010-07-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Naitsirhc Hsem on 2010-07-08
How do I upgrade to Maverick Merecat Development release?

---

### Post by phillw on 2010-07-08
> **Naitsirhc Hsem said:**
> How do I upgrade to Maverick Merecat Development release?

have a read of [http://ubuntuforums.org/showthread.php?t=1522462](http://ubuntuforums.org/showthread.php?t=1522462)

Regards,

Phill.

---

### Post by amauk on 2010-07-09
GUI
```
sudo update-manager -d
```

CLI
```
do-release-upgrade -d
```

---

### Post by ranch hand on 2010-07-09
It would be a real good idea to read the stickies on this forum before you do that (at least the first post of each of them).  It will save you a lot of grief (and us too).

---

### Post by VMC on 2010-07-09
Yes, exactly. I think *Phillw* had the best reply. 

Know what your getting into before you comment to change. 

Especially the last paragraph of his link:
 "...**Once you've started testing, exercise caution when upgrading packages - in special, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade**..."

---

### Post by garvinrick4 on 2010-07-09
I also like phillw's reply.


```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

```

---

### Post by 23meg on 2010-07-10
> **amauk said:**
> GUI
```
sudo update-manager -d
```

CLI
```
do-release-upgrade -d
```

There's no need to run update-manager as root. Just issue ```
update-manager -d
```

---


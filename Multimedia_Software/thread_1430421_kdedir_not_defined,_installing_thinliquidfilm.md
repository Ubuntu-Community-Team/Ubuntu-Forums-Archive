---
title: "kdedir not defined, installing thinliquidfilm"
date: 2010-03-15
forum: Multimedia Software
---

### Post by d4_user on 2010-03-15
Im trying to install thinliquidfilm from the install.py, however i get this error:

```
------------------------------
Clearing old installations ...
------------------------------
Traceback (most recent call last):
  File "./install.py", line 104, in <module>
    if os.path.isfile(kdedir + '/share/apps/konqueror/servicemenu/thinliquidfilm.desktop'):
NameError: name 'kdedir' is not defined

```Anybody ever fixed this?

---

### Post by d4_user on 2010-03-15
fixed.
```

sudo apt-get install konqueror
```

---


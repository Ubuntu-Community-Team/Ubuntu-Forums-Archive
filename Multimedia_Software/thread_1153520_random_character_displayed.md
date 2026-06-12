---
title: "random character displayed"
date: 2009-05-08
forum: Multimedia Software
---

### Post by bangmalley on 2009-05-08
Ever since I followed this [guide]("http://ubuntuforums.org/showthread.php?t=1130582") and installing chinese language support (SCIM), some character will be displayed randomly.
I copy and paste it somewhere, for example, I paste at the search box, it display correctly.

---

### Post by bangmalley on 2009-05-10
solved it by clearing font cache
```

$ cd /usr/share/fonts
$ find . -name fonts.cache-1|xargs rm -f
$ fc-cache .

```

---


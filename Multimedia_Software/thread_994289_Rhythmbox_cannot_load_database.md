---
title: "Rhythmbox cannot load database"
date: 2008-11-26
forum: Multimedia Software
---

### Post by arysar on 2008-11-26
I have reinstalled ubunto 8.04 after an upgrade to 8.10, now I try Rhythmbox and this error appear:

Cannot load database because it was built with a posterior version. This version of Rhythmbox cannot read the database.

Is there any way to delete the database and generate it again.

Thanks

---

### Post by eldragon on 2008-11-26
```

$ rm ~/.gnome2/rhythmbox/rhythmdb.xml

```

---

### Post by arysar on 2008-11-26
Solved, Thank you very much!

---


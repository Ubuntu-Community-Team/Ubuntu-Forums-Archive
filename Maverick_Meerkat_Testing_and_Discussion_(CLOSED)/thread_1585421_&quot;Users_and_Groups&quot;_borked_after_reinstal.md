---
title: "&quot;Users and Groups&quot; borked after reinstall"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-09-30
After a simple daily update totally destroyed my Maverick root partition (details here: [http://ubuntuforums.org/showthread.php?t=1584116](http://ubuntuforums.org/showthread.php?t=1584116)), I reinstalled from the Beta Live CD. I have a separate home partition and re-used the same user data to preserve settings.

After reinstallation (I used reiserfs after the ext4 debacle), everything works fine, except "System -> Administration -> Users and Groups"). I cannot add or edit users, my account is set to "Custom" instead of "Administrators", changes to Groups are accepted but not saved. From the shell, everything works fine.

Any ideas?

---

### Post by recluce on 2010-10-02
*** BUMP ***

Nobody with any idea how to get this resolved?

---

### Post by cariboo on 2010-10-02
My account is set to **Custom** in users & groups, and the groups are the same as when typing:

```
groups
```

There seems to be some changes under the hood, that we aren't aware of, as I can administer vbox without being a member of the vboxusers group.

---


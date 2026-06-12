---
title: "Hash error when upgrading to Mythbuntu 8.04"
date: 2008-02-28
forum: Mythbuntu
---

### Post by Alfaroid on 2008-02-28
I want to upgrade my mythbuntu 7.10 to version 8.04.
When I do this with update-manager -c -d it downloads al the updates execpt one.

I get an hash error on the following:

Failed to fetch [http://mirror.cs.umn.edu/ubuntu/pool/universe/d/db4.3/libdb4.3_4.3.29-11_i386.deb](http://mirror.cs.umn.edu/ubuntu/pool/universe/d/db4.3/libdb4.3_4.3.29-11_i386.deb) Hash Sum mismatch

Does anybody have an idea?

---

### Post by superm1 on 2008-02-28
Try switching to a different mirror

```
sudo software-properties-gtk
```

or pick it from the Applications menu.

---


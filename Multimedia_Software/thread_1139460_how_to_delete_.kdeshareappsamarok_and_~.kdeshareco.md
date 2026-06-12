---
title: "how to delete /.kde/share/apps/amarok and ~/.kde/share/config/amarokrc ...?"
date: 2009-04-27
forum: Multimedia Software
---

### Post by samuraitor on 2009-04-27
hi there,

How do I go about deleting /.kde/share/apps/amarok and ~/.kde/share/config/amarokrc files?

I have logged in as a root in the terminal to find and delete them but I am not able to find them.

Do I login as a root user or normal user?

is it "dotkde" or kde4...?

---

### Post by dentaku65 on 2009-04-27
> **samuraitor said:**
> hi there,

How do I go about deleting /.kde/share/apps/amarok and ~/.kde/share/config/amarokrc files?

I have logged in as a root in the terminal to find and delete them but I am not able to find them.

Do I login as a root user or normal user?

is it "dotkde" or kde4...?

```
sudo updatedb
```
```
locate amarokrc
```
```
locate amarok |more
```
:)

---


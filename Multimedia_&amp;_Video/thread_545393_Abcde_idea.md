---
title: "Abcde idea"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by washegon on 2007-09-07
Hey,

Looking for a way to show a progress bar when abcde is running, I've got it set to autorun when I insert an audio cd, but I'd like to know it's progress visually.  Maybe some script with zenity?

Thanks for the help

---

### Post by andrew.46 on 2007-09-11
Hi,

 Sounds like a great idea and I wish I had the skills to implement it :-) In the meantime I assume you have added the following to your ~/.abcde.conf:

```
    EXTRAVERBOSE
              If set to "y", some operations which are usually  now  shown  to
              the  end  user  are  visible,  such  as CDDB queries. Useful for
              initial debug and if your network/CDDB server is slow.
```

 It does not make a *huge* difference but tends to show a little more.

                        Andrew

---


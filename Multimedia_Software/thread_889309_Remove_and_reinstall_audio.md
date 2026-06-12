---
title: "Remove and reinstall audio"
date: 2008-08-14
forum: Multimedia Software
---

### Post by anathema415 on 2008-08-14
So I completely borked my sound up somehow (see [http://ubuntuforums.org/showthread.php?t=888285]("http://ubuntuforums.org/showthread.php?t=888285")). Is there a way I could remove all the audio stuff from my system and reinstall it so I won't have to reformat and install Ubuntu again. Or re-install the base system without losing everything?

---

### Post by kpkeerthi on 2008-08-14
```

sudo aptitude reinstall ubuntu-desktop

```

---

### Post by markbuntu on 2008-08-14
One thing you could try before you reinstall. Make a new user and then login with that name. This will give you a clean default setup and works for lots of people. You can also try logging in in gnome safe mode and see if your sound works.

---


---
title: "Xine crashes on startup"
date: 2012-06-11
forum: Multimedia Software
---

### Post by PaulM1985 on 2012-06-11
Hi

Sorry I can't be more descriptive than this.  Xine is crashing on startup with a segfault.  Here is my output when I run from terminal:

```

paul@paul-desktop:~$ xine
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
Segmentation fault

```

Any suggestions?

Paul

---

### Post by PaulM1985 on 2012-06-14
Bump.  Any ideas to solve this?

I am guessing that maybe it is a corrupt setup file or something.  Does anyone know anything about this, or as a last resort, how to do a full uninstall and re-install of xine?

Paul

---

### Post by mc4man on 2012-06-14
You may want to mention what release of Ubuntu you are using
xine (xine-ui) works ok here in 12.04 & 12.10 Ubuntu

Maybe try deleting ~/.xine/catalog.cache or just the whole .xine folder itself

---

### Post by PaulM1985 on 2012-06-15
I am using Ubuntu 10.04.  Xine has been working fine for ages.  All of a sudden it started crashing on start up, that is why I thought it could be some configuration file or something.  I will try your suggestion and see what happens.

Thanks

Paul

---

### Post by PaulM1985 on 2012-06-20
> **mc4man said:**
> You may want to mention what release of Ubuntu you are using
xine (xine-ui) works ok here in 12.04 & 12.10 Ubuntu

Maybe try deleting ~/.xine/catalog.cache or just the whole .xine folder itself

I have tried this and I am still getting segfaults.  Any other suggestions?

Paul

---

### Post by PaulM1985 on 2012-06-26
bump?

---

### Post by Hari5g900 on 2012-06-26
Why not try installing vlc? It does everything xine can do and it is a lot more updated.

---


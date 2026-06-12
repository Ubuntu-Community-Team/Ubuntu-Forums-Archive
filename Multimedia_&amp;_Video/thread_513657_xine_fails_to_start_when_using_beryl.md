---
title: "xine fails to start when using beryl"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by gnychis on 2007-07-30
Hi,

I am running Feisty Fawn with Beryl and xfce4.  Everything works great, except for xine.  Xine works just fine when I use FVWM, but not when I'm using Beryl, I get this error trying to start it:
```

gnychis@monster:~$ xine
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
xiTK WARNING(_x_error_handler:258): X error received: 'BadWindow (invalid Window parameter)'
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x1000051
  Serial number of failed request:  42
  Current serial number in output stream:  42

```

I'm not sure where to begin with this, I've tried googling and searching here and have found others with the problem, but no solution yet.

gxine seems to work just fine, however.

Thanks!
George

---

### Post by Andrew-buntu on 2007-08-01
Have you tried starting xine with the command line option for OpenGL output?
```
xine -V gl2 {mymovie}
```

---

### Post by gnychis on 2007-08-01
thanks for the response! but it still returns me the same error :\

---

### Post by trincamckee on 2007-09-15
I actually have the exact same problem, when using beryl, it gives me the same output...
Does anyone have some resolution or something?

Take care

---

### Post by 12jewels on 2007-09-22
I get that same exact error too. We could really use some help. It's the only thing keeping my system from being perfect.

---

### Post by gnychis on 2007-09-22
just reporting that i was never able to solve it... tried the xcomposite forum too, but since beryl merged with compiz they don't really seem to care

---


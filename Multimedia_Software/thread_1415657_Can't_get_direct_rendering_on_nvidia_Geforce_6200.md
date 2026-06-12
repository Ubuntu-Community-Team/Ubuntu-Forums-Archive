---
title: "Can't get direct rendering on nvidia Geforce 6200"
date: 2010-02-25
forum: Multimedia Software
---

### Post by saltydog on 2010-02-25
On Karmic, Nvidia Geforce 6200 and nvidia drivers v. 185, I can't get direct rendering (neither user nor root):

 ```
glxinfo | grep direct
 direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

```
sudo glxinfo | grep direct
 direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

From the log:

```
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"

```

So, modules are loaded. What can I do do enable direct rendering?

running the command:

```
LIBGL_DEBUG=verbose glxinfo
```

I can't find anything wrong, excepts it is reporting a different GeForce model (mine is 6200):

```
OpenGL renderer string: GeForce 7300 LE/PCI/SSE2
```


Thanks for any help

---

### Post by saltydog on 2010-02-25
Sorry, my fault. I was checking thru ssh on a wrong display!

```

DISPLAY=:0 glxinfo | direct
direct rendering: Yes
```

---


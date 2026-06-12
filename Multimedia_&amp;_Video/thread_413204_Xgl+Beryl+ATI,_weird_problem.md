---
title: "Xgl+Beryl+ATI, weird problem"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by IHateSnow on 2007-04-18
I got DRI working fine last time I booted with the default session(gnome+naut....etc.). (ubuntu 6.10)

Now when I start xgl with beryl I'm getting:
```

h@desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

Confirmed by:
```

h@desktop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

The thing is that beryl is working fine. Is this weird that I would get DRI working in one but not the other and beryl still works? 

It's been a little over week that I've been using linux, and I can't believe that I used windows for as long as I did.

---


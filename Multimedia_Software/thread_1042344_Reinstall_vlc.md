---
title: "Reinstall vlc"
date: 2009-01-17
forum: Multimedia Software
---

### Post by honkey on 2009-01-17
If I run vlc, it says there is no skin
if I choose the default skin it dosn't works.
If I reinstall vlc, the same error appears.
if I use purge with apt-get same thing.
How can I get VLC functionally back?

---

### Post by taurus on 2009-01-17
Which release are you running?  Did vlc work before but now wouldn't?

---

### Post by honkey on 2009-01-17
Vlc works until I changed the skin

---

### Post by taurus on 2009-01-17
You can try running it from a terminal with some options.

```
vlc --reset-config
-or-
vlc --ignore-config
-or-
vlc --help <-- for more info
```

---

### Post by cariboo on 2009-01-17
You could just delete vlc from ~/.conf. The next time you start vlc it will be recreated. When uninstalling programs it is best to use complete removal in synaptics or frm the command line use the purge option with apt-get eg:

```
sudo apt-get purge vlc
```

This will completely remove vlc and all it's configuration files.

Jim

---

### Post by binbash on 2009-01-17
i had same problem, purging vlc helped me

---

### Post by honkey on 2009-01-18
Thank you all very much

---

### Post by lamunk on 2010-11-08
logical solution, yet I had to look it up...
thanks for posting :smile:

---


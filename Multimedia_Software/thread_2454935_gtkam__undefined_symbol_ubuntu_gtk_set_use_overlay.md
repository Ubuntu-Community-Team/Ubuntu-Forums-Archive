---
title: "gtkam : undefined symbol: ubuntu_gtk_set_use_overlay_scrollbar"
date: 2020-12-09
forum: Multimedia Software
---

### Post by warmin on 2020-12-09
When I try to start **gtkam** I get the error message:
```
$ gtkam
gtkam: symbol lookup error: /usr/lib/x86_64-linux-gnu/gtk-2.0/modules/liboverlay-scrollbar.so: undefined symbol: ubuntu_gtk_set_use_overlay_scrollbar
```
By the way, I got this message from a few other programs, too ( xsane, xscanimage ).

I have a standard **Ubuntu 20.10** installation.

---

### Post by mc4man on 2020-12-12
Certainly doesn't seem like a "standard Ubuntu 20.10 installation. "
Why do you have overlay-scrollbar-gtk2 installed in the 1st place?
( though there is no reason for gtkam in 20.10 to use anyway..

---

### Post by warmin on 2020-12-21
Thanks for your answer. Since some releases I do not something special beside upgrading to the next Ubuntu release. But your hint lead me to remove overlay-scrollbar-gtk2. Now I still get a warning, but at least the app starts. What's behind "there is no reason for gtkam to use"?

---


---
title: "How to reduce video RAM use?"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by althus on 2007-04-25
Hi all.  I've got a lousy old laptop that I've made work with Xubuntu Edgy, and am thankful for that.  But it still freezes sometimes in X.  Reducing the display size to 800x640 (or whatever exactly it is) helps, but they still happen, though less often.  There is one application I *need* to work in X, and it is what still freezes sometimes.  So.

What can I do to minimize video RAM usage by X?  I've maxed out what I can configure in the BIOS.  I think I should set default runlevel to the command shell, and then use xinit or startx to run this app.  

Is there any configuration of X I can do to absolutely minimize its video ram use after that?

Thx.

---

### Post by mthakur2006 on 2007-04-25
try 
```
 sudo dpkg-reconfigure xserver-xorg 
```

---


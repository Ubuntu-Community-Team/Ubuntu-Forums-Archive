---
title: "Window border mirrored"
date: 2008-10-12
forum: Multimedia Software
---

### Post by b4rt on 2008-10-12
Hi,

I recently installed the mac4lin theme.
Now, when I switch back to the original Human theme, my window border is mirrored, like the X button to shutdown the program is on the left instead of on the right.

Also, gnome complains about not having the gtk+ theme engine when using the mac4lin theme... I have searched for it, but I cannot find anything :(

Thanks in advance,

B4rt

---

### Post by b4rt on 2008-10-13
Hey, thank B4rt, this totally fixed the problem for me:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"
```

Thanks B4rt!

---


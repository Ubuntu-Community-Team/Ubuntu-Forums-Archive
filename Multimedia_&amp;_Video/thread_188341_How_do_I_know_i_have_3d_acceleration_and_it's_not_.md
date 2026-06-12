---
title: "How do I know i have 3d acceleration and it's not my proc?"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by zahidism on 2006-06-03
when I run glxgears and the like my CPU usage cranks to full and I'm a wee bit worried that after installing the fglrx drivers im still not using 3d.

---

### Post by ajack on 2006-06-04
[QUOTE=zahidism]when I run glxgears and the like my CPU usage cranks to full and I'm a wee bit worried that after installing the fglrx drivers im still not using 3d.[/QUOTE]

open a terminal and type:

glxinfo | grep direct

That will tell you if X Windows is using 3D acceleration of you gfx card.  :mrgreen:  

Seriously, if you did a search in the forums, you would have found your answer immediately.

---

### Post by killbill on 2006-06-04
```

libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
direct rendering: Yes

```
but I have a glx fps of 400 or so.  Intel 845G

---

### Post by kaamos on 2006-06-04
```
fglrxinfo
```
The output should **not** contain "mesa".

---

### Post by eqisow on 2006-06-04
Err, maybe I'm being ignorant here, but since when do the fglrx drivers work for intel chipsets?

Also, Intel video chipsets are not good, at all. I wouldn't be surprised if that's all it got in glxgears. Besides, glxgears is not meant to be a benchmark.

---

### Post by ajack on 2006-06-04
[QUOTE=killbill]```

libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
libGL warning: 3D driver claims to not support visual 0x32
direct rendering: Yes

```
but I have a glx fps of 400 or so.  Intel 845G[/QUOTE]

From the looks of it, the i810 (covers the intel graphics family of cards, not just the i810) driver is loaded and trying to run properly.  Your libGL driver is complaining.  I do not know if it's part of mesa or something else.

---


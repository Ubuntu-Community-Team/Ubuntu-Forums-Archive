---
title: "VirtualBox with 2.6.37 failing"
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-12-18
** Updated **

Using a mainline build works around the problem introduced by Ubuntu sauce.


***

[http://forums.virtualbox.org/viewtopic.php?f=15&t=37150](http://forums.virtualbox.org/viewtopic.php?f=15&t=37150)

vboxdrv does not build with kernels >=2.6.37-8; does anyone know of a workaround?

---

### Post by pressureman on 2010-12-18
It was working ok for me up to 2.6.37-9, but I noticed that bug you link to with 2.6.37-10.

It should hopefully be a fairly minor fix.

---

### Post by jfernyhough on 2010-12-19
[http://forums.virtualbox.org/viewtopic.php?f=15&t=37215](http://forums.virtualbox.org/viewtopic.php?f=15&t=37215)

Looks like using a [mainline build]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") gets things working; it's the Ubuntu sauce that is breaking it.

---


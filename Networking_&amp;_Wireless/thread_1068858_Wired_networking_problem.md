---
title: "Wired networking problem"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by mrund on 2009-02-13
With some work, I've gotten my MSI Wind laptop to use wifi reliably. But I can't get a *wired* network connection at the library like I'm used to, where every table has an ethernet socket. It works just fine there when I boot WinXP on the machine.

What are the most common configuration tweaks that will solve this?

---

### Post by odium1 on 2009-02-13
what kernel are you running?

put this in the terminal and post the results:

```
uname -a
```

i'm curious to see if your problem is related to the 2.6.27-11 kernel issue. if so, i know a pretty good solution.

---

### Post by mrund on 2009-02-13
2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

---

### Post by odium1 on 2009-02-15
yeah that's the kernel that is giving everyone so many ethernet problems. i would suggest downloading **kernelcheck** [http://kcheck.sourceforge.net/]("http://kcheck.sourceforge.net/") and letting it compile and install the latest kernel (2.6.28-*).. that is what i had to do to regain eth0 connection

---

### Post by superprash2003 on 2009-02-15
if you still have problems post **ifconfig** output from the terminal

---


---
title: "cinelerra error need help"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by kahram.yoon on 2008-02-18
After opening cinelerra, an error window pos up saying:
void MWindow::init_shim(): WARNING: /proc/sys/kernel/shmmax is 0x2000000, which is too low.
  Before running Cinelerra do the following as root
  echo "0x7fffffff" > /proc/sys/kernel/shmmax

I typed this into the terminal and I got this
-desktop:~$ echo "0x7fffffff" > /proc/sys/kernel/shmmax
bash: /proc/sys/kernel/shmmax: Permission denied

how do i fix this problem?

---

### Post by xc3RnbFO8P on 2008-02-18
> System> Preferences> Main Menu> System Tools> (check box) Root Terminal

Then open Root Terminal in:>  Application>System

In terminal:

> echo "0x7fffffff" > /proc/sys/kernel/shmmax && cinelerra

---


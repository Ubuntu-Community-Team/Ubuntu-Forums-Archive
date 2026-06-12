---
title: "How to disable xserver autostart?"
date: 2008-08-02
forum: Multimedia Software
---

### Post by shaggy999 on 2008-08-02
I've got xubuntu installed on an old PII 333 MHz w/ 160 MB of RAM, but I would prefer to stick to a terminal unless I actually need to run a graphical program. So what I'm wondering is how do I keep xserver from automatically starting?

---

### Post by soxs on 2008-08-28
decrease default runlevel

normally it is defined in /etc/inittab, but ubuntu doesn't use this config file anymore.

So you will have to append a grub setting like:
init 3

---


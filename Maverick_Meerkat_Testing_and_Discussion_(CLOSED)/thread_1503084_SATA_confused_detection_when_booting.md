---
title: "SATA confused detection when booting"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-06-06
i've searched to reduce boot delay with maverick:

- booting without both quiet and splash to see all the verbose process

- found that everything goes well and fast, except when finding and identifying sata internal devices: here is where grub2 is very confused, scanning info done by these weird chipsets: jmicron + ich7r (fakeraid not used) + 975x. The process first test about the fastest sata, dont find it as it does not exist, then fallback to normal sata, and continue to scan for nothing 10/15 more seconds, and finaly fastly end the process and boot.

- looking at logs, i dont see all these details seen during boot on screen, is there a way to add some code into /etc/default/grub to save all the verbose mode ?

- i've tested with kernel 32, 34 and 35: same problem

what do you guys think about possible solutions ?

---


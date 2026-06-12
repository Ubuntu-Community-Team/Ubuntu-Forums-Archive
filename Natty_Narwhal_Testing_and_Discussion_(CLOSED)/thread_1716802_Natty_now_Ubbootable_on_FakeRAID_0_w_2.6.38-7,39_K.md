---
title: "Natty now Ubbootable on FakeRAID 0 w/ 2.6.38-7,39 Kernel"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronparent on 2011-03-29
This has been the case since Saturday.See bug report: [https://bugs.launchpad.net/bugs/744586](https://bugs.launchpad.net/bugs/744586)

Has anyone else seen this regression? It will probably apply to raid5 & raid 10 as well. It applies to both natty upgraded and fresh install from the daily.

---

### Post by ronparent on 2011-03-30
This can be fixed with a workaround. It turns out that both the update or new install lack the dmraid program. Installing dmraid to either permits booting. 

Simply boot the updated installation on an older kernel and install dmraid. For the new install you have to boot into whichever system is booting and chroot the dmrait install to the partition with the new install. I hope the developers fix it for the RC.

---

### Post by Petithomme on 2011-04-18
Fixed on the daily build I installed today (April 18th)

---


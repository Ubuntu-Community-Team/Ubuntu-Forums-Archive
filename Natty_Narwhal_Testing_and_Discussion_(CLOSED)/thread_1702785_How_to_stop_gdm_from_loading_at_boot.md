---
title: "How to stop gdm from loading at boot"
date: 2011-03-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2011-03-08
I am actually running kubuntu with kdm and the kde desktop. For some reason, gdm starts on bootup, and seems to be bringing in other programs along with it (orca) that generate errors. I remember from previous problems that somewhere in the startup files is a way of stopping gdm from starting, since it isn't needed and just causes errors. I don't want to remove gdm altogether, because gnome and unity won't run without it. Any idea how to stop it from running automatically? I suppose this is really a kubuntu question, but folks here are probably more familiar with gdm. Thanks.

---

### Post by dino99 on 2011-03-08
if kdm is installed and you login with it, open synaptic to uninstall gdm, an other way is to deselect it into "services"

---

### Post by doctordruidphd on 2011-03-08
1. Uninstalling gdm is not an option, for reasons mentioned in the OP.

2. gdm is not listed in kdm's service manager. I believe it is being started through upstart, before kdm starts. There is a script somewhere that is supposed to check whether another manager is being run, and if not, starts gdm. So far I have not been able to find it.

---

### Post by dino99 on 2011-03-08
> **doctordruidphd said:**
> 1. Uninstalling gdm is not an option, for reasons mentioned in the OP.

2. gdm is not listed in kdm's service manager. I believe it is being started through upstart, before kdm starts. There is a script somewhere that is supposed to check whether another manager is being run, and if not, starts gdm. So far I have not been able to find it.

As i dont use KDE i cant give an exact answer, but i think you might report against that issue. If your system is a pure KDE system not mixing gnome apps, you should not meet such problem.

---

### Post by zika on 2011-03-08
I think that, simply, moving /etc/init/gdm.conf and /etc/init.d/gdm to a safe place, other than /etc/init and /etc/init.d could do the trick...
Once You need gdm again, simply, put thet back to their place(s)...

(That is the way I &#8222;turn off&#8220; plymouth, NM, apparmor etc...)

---

### Post by doctordruidphd on 2011-03-08
Yep, sometimes the simplest things work the best.

At least it stopped orca from spewing error messages.

Thanks.

---


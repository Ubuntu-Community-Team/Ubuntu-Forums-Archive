---
title: "Nvidia drivers on Quantal"
date: 2012-10-20
forum: Multimedia Software
---

### Post by nerdkiller14 on 2012-10-20
When I install nvidia drivers I get 

"could not load /lib/modules/3.2.0-29-generic/modules.dep" 

I have kernel 3.5 from Quantal and this seems to be the problem but I can't fix it. Any Ideas?

---

### Post by pqwoerituytrueiwoq on 2012-10-20
how are you installing the driver?
i have not had any  issues installing nvidia driver for the repos (stock and xorg edgers)

---

### Post by nerdkiller14 on 2012-10-22
> **pqwoerituytrueiwoq said:**
> how are you installing the driver?
i have not had any  issues installing nvidia driver for the repos (stock and xorg edgers)

Sudo apt-get install nvidia-current nvidia-settings 

Is there anyway for me to change what kernel the drivers use?

---

### Post by pqwoerituytrueiwoq on 2012-10-22
it will use what ever kernel you are running at install
if you are asking for a installer for the 3.6.x kernel i can post a installer here for you
edit:
i had this problem one before, the symlinks are messing up, most likely during the upgrade from 12.04
there are 4 symlinks in /
initrd.img
initrd.img.old
vmlinuz
vmlinuz.old
you just have to make them point to the correct location

---


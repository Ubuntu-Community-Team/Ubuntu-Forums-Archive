---
title: "Virtualbox 4.0.2 with kernel 2.6.38 can't builder driver"
date: 2011-01-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by feiy on 2011-01-31
feiy@feiy-laptap:~/Desktop$ uname -a
Linux feiy-laptap 2.6.38-020638rc2-generic #201101220905 SMP Sat Jan 22 09:09:13 UTC 2011 x86_64 GNU/Linux
feiy@feiy-laptap:~/Desktop$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                               *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  
 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
feiy@feiy-laptap:~/Desktop$ cat /var/log/vbox-install.log 
Makefile:178: *** Error: /usr/src/linux (version 2.6.38-rc2) does not match the current kernel (version 2.6.38-020638rc2-generic)&#12290; stoped&#12290;


i hava done the <linux/autoconf.h> bug's fixed!

---

### Post by dino99 on 2011-01-31
it fail on my end too

---

### Post by alexsb on 2011-01-31
@feiy - could you go into some detail how you fixed the issue?

thanks,

alex

---

### Post by feiy on 2011-01-31
i have not fixed this bug,just do some 2.6.38 's bug fixed,but the error don't fixed

---

### Post by bruno666 on 2011-01-31
You should have a look to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/705593").

---

### Post by jfernyhough on 2011-01-31
> Error: /usr/src/linux (version 2.6.38-rc2) does not match the current kernel (version 2.6.38-020638rc2-generic)

It sounds like an issue with your .38-rc2 kernel headers. Try reinstalling them, or removing them and boot with the .38-1 natty kernel.

---

### Post by Le Gluon du Net on 2011-02-01
> **bruno666 said:**
> You should have a look to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/705593").

Thank you Bruno, on this page I found this command:

```
sudo find /usr/share/virtualbox/src/vboxhost -name *.h -exec perl -pi -w -e 's/linux\/autoconf/generated\/autoconf/g;' {} \;
sudo /etc/init.d/vboxdrv setup

```

wich resolved the problem.

LGDN

---

### Post by c0rrupt on 2011-04-24
This doesn't solve the problem for me.  Does anyone know of another fix that might work?

> **Le Gluon du Net said:**
> Thank you Bruno, on this page I found this command:

```
sudo find /usr/share/virtualbox/src/vboxhost -name *.h -exec perl -pi -w -e 's/linux\/autoconf/generated\/autoconf/g;' {} \;
sudo /etc/init.d/vboxdrv setup

```

wich resolved the problem.

LGDN

---

### Post by Hedgehog1 on 2011-04-25
Old Thread...

If you are running Virtual Box in **Natty**, you need to run version 4.0.6 (just released a few days ago).

***The Hedge***

:KS

---


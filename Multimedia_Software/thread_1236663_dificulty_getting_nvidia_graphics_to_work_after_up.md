---
title: "dificulty getting nvidia graphics to work after updates"
date: 2009-08-10
forum: Multimedia Software
---

### Post by Lorenzo1985 on 2009-08-10
Hi

I've been trying to do some bits including an upgrade from 2.6.28-11 to the 2.6.28-15. Now i'm having some major issues getting the Nvidia driver working. 

When I've wanted to use the nvidia driver before i have simply selected the latest version in jockey. But at the moment it seems to only be offering me just "nvidia" and selecting that doesnt do anything, it just processes for a while and never gets there. and never selects activated.

Does anyone have any idea what's going on?

[CENTER][IMG]http://www.protazoa.com/Hardware_Drivers.png[/IMG][/CENTER]

```
loz@gravity:~$ dpkg --get-selections  | grep nvidia                                                   nvidia-180-kernel-source                        install
nvidia-180-libvdpau                             install
nvidia-180-libvdpau-dev                         install
nvidia-180-modaliases                           install
nvidia-glx-173                                  deinstall
nvidia-glx-180                                  install
nvidia-glx-180-dev                              install
nvidia-glx-71                                   deinstall
nvidia-settings                                 install
```

```
loz@gravity:~$ uname -a
Linux gravity 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 x86_64 GNU/Linux
```

---

### Post by dagrump on 2009-08-10
Well, have you rebooted? You need to reboot after installing the drivers.

---

### Post by Lorenzo1985 on 2009-08-11
Firstly thanks for your time dagrump!!


Unfortunatly I can only wish it was that easy, I've been rebooting after every change but to no avail?

Anyone else got any good ideas what it might be or things i can check?

---


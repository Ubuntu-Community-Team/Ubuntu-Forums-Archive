---
title: "NO VIDEO!! Please help can't see desktop!!"
date: 2010-09-16
forum: Multimedia Software
---

### Post by popppppz on 2010-09-16
I was having problems running opengl after an update from Kubuntu 10.04 to Meerkat 10.10.  I used Package Manager to remove xconfig or or something, and install a different version.  Now I can only see up to the blue Kubuntu loading screen, I cannot see my desktop or custom loading screen that comes after.  Please help! I am using a Toshiba laptop with the 64 bit version of Kubuntu Linux Maverick Meerkat 10.10 fully updated, and I have an Intel Mobile Express 945 graphics onboard video.  I am also triple booting Windows XP and Windows 7 with Linux.

---

### Post by Yellow Pasque on 2010-09-16
Boot to recovery mode, re-install whatever you removed. Maybe these commands will help:
```
sudo apt-get install --reinstall xserver-xorg-video-intel xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by popppppz on 2010-09-16
hi thanks, it says no such file or directory for ect/xll/xorg.conf

---

### Post by Yellow Pasque on 2010-09-16
lInuX iS cASe SenSITiVe

---

### Post by popppppz on 2010-09-16
i did it again and i get the same message and i checked it a bunch of times its written exactly as you typed it

---

### Post by popppppz on 2010-09-16
sudo apt-get install --reinstall xserver-xorg-video-intel xserver-xorg-core when i type this code i also get a error;
Errors were encountered wile processing:
fglrx
fglrx-amdcccle
xorg-driver-fglrx
Sub-process /user/bin/dpkg returned an error code(1)

---

### Post by popppppz on 2010-09-16
THANKS! I just deleted one of those files using sudo get-apt remove, i relised it was a radeon driver and now im back up and running! thanks for pointing me in the right direction =D

---


---
title: "Graphic Problem? Please Help Me?!"
date: 2008-07-30
forum: Multimedia Software
---

### Post by moorara on 2008-07-30
i'm beginner in linux. i have installed my graphic card with "nvidia-glx-new.deb" package by "Hardware Drivers Manager".
every time i boot with ubuntu and login to my user by KDE session my resolution automatically changed to default. i tried to change the resolution by "NVIDAI XServer Settings" tools but the next time i login, resolution changes to default value.
please help me!

---

### Post by pietjanjaap on 2008-07-30
Tru this:

With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---


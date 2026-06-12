---
title: "resolution stuck at 800x600 after ubuntu update"
date: 2008-06-21
forum: Multimedia Software
---

### Post by kaston on 2008-06-21
i have an nvidia geforce 7600 chip on my toshiba satellite laptop and i am running gutsy.  i ran an ubuntu update this morning like i often do only this time it said i needed a reboot which i thought was odd since it had never asked me to do this before.  i did it anyways and rebooted and then it said that i had to use low graphics mode because my screen and graphics cards could not be detected correctly.  it says that i have to configure the display myself but i have no idea how.  now i am stuck at 800x600.  i took a look at my xorg.conf and noticed that there was nothing higher than "800x600" listed so i tried overwriting my xorg.conf with a previous version that had "1260x800" in it.  but that didn't work.  i also tried uninstalling and reinstalling nvidia drivers using envy.  any ideas how to get my resolution back?

problems like this are really making me consider going back to windows.  sure i had viruses but at least i could see them on a normal sized screen.

---

### Post by Novus on 2008-06-21
I was also stuck at low res after some updates in hardy.. I downloaded nvidia-settings from the repos and was able to change my settings there.

---

### Post by kaston on 2008-06-21
i have nvidia settings and tried that too but there isn't any option in the window to pick a higher res

---

### Post by kaston on 2008-06-21
anyone?  i really need my normal res in order to do work properly

---

### Post by pietjanjaap on 2008-06-22
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---


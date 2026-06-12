---
title: "[SOLVED] Restricted Drivers Manager seems lost..."
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by Quilzas on 2007-08-23
In effort to get my Nvidia FX 5200 drivers installed, I installed the Restricted Drivers Manager.

It is listed as being installed, but I cannot find it.  It is not listed anywhere.. I´ve looked in all the menus and submenus.  There is no admin menu anywhere in the K Menu or the System Menu.  I can´t find a way to add the admin menu.  I´ve reinstalled the Restricted Drivers Manager a couple of times, but still, it´s not appearing anywhere.


Ideas?  Anyone?
I´ve searched high and low and can´t find it nor help online.


(running Kubuntu 7.04...)

---

### Post by tseliot on 2007-08-23
type:
```
restricted-manager
```

---

### Post by Quilzas on 2007-08-23
Okay, that worked (well, it spat out some errors but still opened).  Of course, the nvidia restricted drivers were already in use, and I still can´t change my screen resolution past 1024x768 (which is goes past that find in windows.. dual boot system).

It was suggested to check what drivers it was using for my monitor, and it´s just using default plug-n-play drivers.  But there doesn´t seem to be anything better to change that to (my monitor is not in the manufacturer´s list).

---

### Post by tseliot on 2007-08-23
type:
```
sudo nvidia-settings
```

and set the resolution

---

### Post by Quilzas on 2007-08-23
Whoa.  That worked!!

Thanks!!!!!!!!


I swear, it´s the little things.  :)

---

### Post by akba0012 on 2007-08-23
Sweet! worked for me too! thanks!

---


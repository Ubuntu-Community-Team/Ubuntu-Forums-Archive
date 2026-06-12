---
title: "X Server not configured correctly"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by Liamkerrigan on 2007-08-22
okay im running Ubuntu 7.04, i recently just got it up and running, downloaded all of the appropriate Ubuntu updates. I then went and decided to have a look at desktop effects.. i clicked enabled driver, and it downloaded some update and told me i needed to restart on booting up my computer again i clicked on Ubuntu (I'm dual booting windows xp and Ubuntu 7.04), and it came up with a black screen which then changed to a kind of blue screen with and error message saying-  

"failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" ( i clicked yes) and said some things about failing to initialize the nvidia graphics device. 

I am running a dell dimension e520 
EVGA Geforce 8800GTS 640mb
Dual booting ( XP, Ubuntu 7.04)

---

### Post by tseliot on 2007-08-22
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

---

### Post by pkarlos_76 on 2007-08-24
Tsel, your solution still leaves him without nvidia 3d accelleration?

---

### Post by tseliot on 2007-08-24
> **pkarlos_76 said:**
> Tsel, your solution still leaves him without nvidia 3d accelleration?
yes, but at least he will have access to the Desktop again

---


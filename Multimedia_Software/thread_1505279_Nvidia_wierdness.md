---
title: "Nvidia wierdness?"
date: 2010-06-08
forum: Multimedia Software
---

### Post by redcodefinal on 2010-06-08
Hi,
I booted up my desktop today to find Ubuntu somehow lost my video driver. It told me that ubuntu had to run in low graphics mode because it lost my configuration. I rebooted my computer and suddenly everything was working fine. Or so I thought. Now I can't get the extra desktop effects to work. (Jiggly windows and such :D) I decided to take a peek inside my nividia X server settings and saw that there was no config file. I created one but, the problems still persist. Also, I don't know if this helps but, for some reason everytime I boot into ubuntu and log in it gives an error along the lines of "couldn't update /home/username/.ICEAuthority" or something. Please help!?!?!

---

### Post by Jinger on 2010-06-09
What about X11?

---

### Post by redcodefinal on 2010-06-10
> **Jinger said:**
> What about X11?
What is X11?

---

### Post by Jinger on 2010-06-10
If you are on Ubuntu, use this command:
```
gedit /etc/X11/xorg.conf
```and copy and past the results here.

---


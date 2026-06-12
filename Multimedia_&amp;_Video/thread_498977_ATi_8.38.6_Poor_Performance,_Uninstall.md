---
title: "ATi 8.38.6 Poor Performance, Uninstall?"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by chaoticblankness on 2007-07-12
I installed the latest ATi drivers (8.38.6) thinking I would get better performance, and I was very wrong.

Even OpenGL screen savers are less than 5 FPS now.  If there is any way to fix this I'd like to know, but if not I would like to know how uninstall them and return to the "Restricted Drivers" offered through Ubuntu.

---

### Post by spidernik84 on 2007-07-12
> **chaoticblankness said:**
> I installed the latest ATi drivers (8.38.6) thinking I would get better performance, and I was very wrong.

Even OpenGL screen savers are less than 5 FPS now.  If there is any way to fix this I'd like to know, but if not I would like to know how uninstall them and return to the "Restricted Drivers" offered through Ubuntu.
I second that, same problem here, the performance degradation is quite noticeable.
Nice one AMD/Ati, like the prawns: walkin' backwards...[-X

---

### Post by spidernik84 on 2007-07-12
Update: I've found the way reading ati's official readme (why didn't i found this part before?)

Here what the readme suggests:

> 
Uninstalling the ATI Linux Proprietary Graphics Driver

Un-installing the ATI Linux Proprietary Driver is dependent on the mode of initial installation.
Automatic or Custom Driver Installations

If the ATI Proprietary Linux Graphics Driver was installed using either the Automatic or Custom options, then do the following:

   1. Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
   2. With super user permissions, enter the command "**sh ./fglrx-uninstall.sh**" 

You have now successfully uninstalled the ATI Linux Proprietary Graphics Driver.
Package Generation

If the initial installation of the driver was done via the Operating Systems package management software (rpm, apt, etc.) then please use that package management software to remove the ATI Proprietary Linux Graphics Driver. 


---


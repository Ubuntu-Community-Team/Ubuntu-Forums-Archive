---
title: "Graphics Driver Problem"
date: 2009-11-09
forum: Multimedia Software
---

### Post by MHail on 2009-11-09
Hey guys I just installed Ubuntu and I can not log in with a graphical interface. When I click on my screen everything freezes but my mouse and I get this graphical glitch on my screen. My computer has done this with every distro I've tried. The only thing that keeps this from happening is starting in safe graphics mode. What fixed the problem on my last and only distro I was able to get installed, was installing the latest nvidia graphics drivers for my 7800 GT. Is there any way to install drivers without logging in, or to load in safe graphics mode?

---

### Post by RavanH on 2009-11-09
have you tried to add acpi=off as kernel boot switch in GRUB ? with that, you might just get into X to comfortably update the driver (or revert to a generic one)

---

### Post by markbuntu on 2009-11-10
Just so you know, if you have a problematic gpu, like the 7800, you should install in safe graphics mode (F4 from the very first screen to select that). Many distros have buggy proprietary drivers in their isos and this will avoid them and use the generic VESA driver which works with all gpus.

After the install is finished reboot and then get all the updates and reboot again before trying to install the proprietary driver. A lot of the broken drivers were fixed in updates so getting updates before trying to use them is critical to success.

If your install is kludged you can try the recovery kernel from the grub menu and then use the fix x option which will attempt to invoke the VESA driver but this may or may not work because ATI and Nvidia proprietary drivers replace many parts of the x-server.

---


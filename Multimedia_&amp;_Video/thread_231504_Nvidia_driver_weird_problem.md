---
title: "Nvidia driver weird problem"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by kernco on 2006-08-07
I have a GeForce 5500 and Ubuntu 6.06.  I installed the drivers and they work, but whenever I reboot the computer, gdm fails to start with the message "Error: API mismatch: the NVIDIA kernel module has the version 1.0-7174, but this X module has the version 1.0-8762.  Please make sure that the kernel module and all NVIDIA driver components have the same version."

That error makes perfect sense until you look at the driver installer I downloaded which is called "NVIDIA-Linux-x86-1.0-8762-pkg1.run", so it should have the correct version.  The weird part is that if I can fix it by executing the installer.  I don't even have to reinstall the drivers, I can just choose "Do not accept" for the terms of license when they appear, and then gdm will start.  I have to do this everytime I boot, though, which is getting annoying.

---

### Post by tseliot on 2006-08-07
Try my Envy script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by pcraven on 2006-09-08
I have the exact same issue. I didn't realize until I read your post that I could skip the install step and just say 'no' to the terms. Did you ever find a way around it?

---


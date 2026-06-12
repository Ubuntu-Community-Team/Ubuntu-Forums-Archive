---
title: "Cannot Open Downloaded nVidia 86 96.43.11 Driver for Install"
date: 2009-05-17
forum: Multimedia Software
---

### Post by billtoliver on 2009-05-17
I am new to Ubuntu.  I recently installed Jaunty 9.04, but had problems with the video/graphics resolution from my GeoForce 4MX420 card.  I downloaded the latest version of the driver from the nVidia website on Firefox.  When I attempted to open the driver from the download box, I could not determine which program I needed to open it.  When I attempted to run the install command on the terminal, I got a massage that it was unable to open the driver.  I desperately, need instructions on how to open the driver so that I can try  to install the new driver.  Any assistance will be greatly appreciated.  Below is a copy of the command prompts:

:~$ sh NVIDIA-Linux-x86-96.43.11-pkg1.run
sh: Can't open NVIDIA-Linux-x86-96.43.11-pkg1.run
:~$

:confused:

---

### Post by 67GTA on 2009-05-17
Right click on the .run file, click properties, select the permissions tab, and make sure the "Execute" box is checked. Then try it again with sudo.

```
sudo sh NVIDIA-Linux-x86-96.43.11-pkg1.run
```

---

### Post by 67GTA on 2009-05-17
There are also some handy tips here for installing manually from Nvidia in case you have trouble afterwards:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---


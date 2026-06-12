---
title: "Nvidia problems :("
date: 2006-01-27
forum: Multimedia &amp; Video
---

### Post by Aphopis on 2006-01-27
Hello!
I recently bought a used nvidia geforce 4200Ti graphics card (before i had a radeon 9250) and when i booted into kubuntu, xorg wouldn't start...so i first tried to apt-get the drivers. They installed nicely but wouldn't work, so i downloaded the latest from nvidia.com and installed that (put the NVIDIA-Linux-x86-1.0-8178-pkg1.run in /usr/src). This package installed fine, x started and everything but when i play games (like enemy territory) my computer freezes (only in ET, quake3 works great and only if i play for a long time) and when i reboot i have to reinstall the driver becouse X wouldn't start up :o
In the log it says that no nvidia driver was found (nvidia.ko). What could be the problem? I unnistaled ati drivers, but didn't delete any modules, must i delete them?
I thank you for your help

p.s. Hope there was no other thread like this and that my bad english isn't annoying anyone :)

---

### Post by mo_x on 2006-01-27
I suspect you didn't remove the driver you installed with apt-get completely.
Here is a short howto for installing the latest nvidia driver.
- Install compiler etc. and linux headers.
```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo apt-get instal gcc-3.4
```
- Remove all packages related to nvidia driver with --purge option
```
sudo dpkg --purge nvidia-glx
sudo dpkg --purge nvidia-kernel-common
sudo dpkg --purge linux-restricted-modules-`uname -r`
```
- Run the installer script (you may need a different version).
```
export CC=/usr/bin/gcc-3.4
sudo sh NVIDIA-Linux-x86_64-1.0-8178-pkg2.run
```

---

### Post by codejunkie on 2006-01-27
[QUOTE=Aphopis]Hello!
I recently bought a used nvidia geforce 4200Ti graphics card (before i had a radeon 9250) and when i booted into kubuntu, xorg wouldn't start...so i first tried to apt-get the drivers. They installed nicely but wouldn't work, so i downloaded the latest from nvidia.com and installed that (put the NVIDIA-Linux-x86-1.0-8178-pkg1.run in /usr/src). This package installed fine, x started and everything but when i play games (like enemy territory) my computer freezes (only in ET, quake3 works great and only if i play for a long time) and when i reboot i have to reinstall the driver becouse X wouldn't start up :o
In the log it says that no nvidia driver was found (nvidia.ko). What could be the problem? I unnistaled ati drivers, but didn't delete any modules, must i delete them?
I thank you for your help

p.s. Hope there was no other thread like this and that my bad english isn't annoying anyone :)[/QUOTE]
how were you able to install the drivers by just placing the NVIDIA-Linux-x86-1.0-8178-pkg1.run file in your /usr/src directory if that's all you did they shouldn't be working :-k could you give me a short walk through on how you installed the NVIDIA-Linux-x86-1.0-8178-pkg1.run file you downloaded from [www.nvidia.com](www.nvidia.com)

---

### Post by Aphopis on 2006-01-27
i placed it in /usr/src the i cd in the directory and run ./NVIDIA-Linux-x86-1.0-8178-pkg1.run
Then i just follow the procedure to the end and when it configures xorg and i type startx it works....

---

### Post by Aphopis on 2006-01-27
Uh removing with --purge did the trick, glx was still installed. Now i tried to reboot and the X started up normaly :mrgreen: 
Thank you all for your advice, you are the best

---


---
title: "ati radeon 9800 driver wond read on fglrxinfo"
date: 2008-10-12
forum: Multimedia Software
---

### Post by adamb24 on 2008-10-12
Heres the problem. I have an ati radeon 9800 pro graphics card and im trying to enable it to be able to use compiz fusion and the other opengl capabilities. I tried installing it manually, through the proprietary drivers, and through envy. Each time it still reads mesa inderect rendering when i type in fglrxinfo on the terminal. And anytime i try to select extra in the desktop preferences the screen goes white. Does anyone know how to fix this? right now it just reads fglrx not installed when i type it in the terminal.

---

### Post by adamb24 on 2008-10-12
bump

---

### Post by adamb24 on 2008-10-15
bumping again, please someone help

---

### Post by BMWDriver on 2008-10-15
Hi,
I've had those problems too. The driver had turned out not to be properly installed. So, my cure was visiting the [Unofficial ATI Driver Wiki]("http://www.wiki.cchtml.com/") where I found well organized information on how to verify the install, troubleshoot and installation.

So, the Mesa thing means the driver was not properly installed. You will find everyhing you need on the link above. 

My suggestion after that is that you go in the configuring section once the driver works, and enable 2D acceleration. This will allow the use of the video rendering engine on the card and give better video output, especially when upscaling.

Good luck !

---

### Post by porchrat on 2008-10-15
BMWdriver's link is not functional for some reason.  There is some info on the mesa driver issue and some possible actions that can be taken here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---


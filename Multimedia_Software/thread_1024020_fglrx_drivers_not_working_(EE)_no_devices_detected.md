---
title: "fglrx drivers not working (EE) no devices detected"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Dark_Sabre on 2008-12-28
I have tried every way possible to install these drivers for my Radeon 9200 pro card, but when it starts up, I get the error message "(EE) No devices detected" or something similar. Is there any way to get this to work or is there an alternate driver?

---

### Post by ajgreeny on 2008-12-28
I used to use the fglrx driver in a previous ubuntu version, but can't remember which one.  It was very little different in fact to the open source ati driver which will have been installed by the system at installation of ubuntu on your machine, and certainly the drivers now available through the Restricted Drivers utility do not work with the 9200 card.  If you really want to bother you will need to search for the legacy driver 8.28.8 on ati's website and install it manually, but last time I tried that I got nowhere at all and gave up.

---

### Post by Dark_Sabre on 2008-12-28
Hmm.... I would like to get some 3D support at the moment, as i'm trying to run Halo in wine. Does this legacy driver have 3D?

---

### Post by markbuntu on 2008-12-28
The Radeon Driver now fully supports that card in the newer versions. 

[http://www.radeonhd.org/](http://www.radeonhd.org/)

---

### Post by ajgreeny on 2008-12-29
@ DarkSabre
You should have 3d support with the driver that was in place after installing ubuntu.  In a terminal run ```
glxinfo
``` and near the top of the output there should be a line saying 
```
direct rendering: yes
```
If so you have full card support and all is well.

---


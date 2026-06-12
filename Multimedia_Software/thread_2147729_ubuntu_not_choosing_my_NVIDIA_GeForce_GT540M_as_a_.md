---
title: "ubuntu not choosing my NVIDIA GeForce GT540M as a default GPU"
date: 2013-05-22
forum: Multimedia Software
---

### Post by helixo on 2013-05-22
output of lspci | grep VGA 


```


00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


``` 


even if i have a NVIDIA GeForce GT540M 2GB GPU , there is no way that ubuntu asserts it , or knows about it , or acknowledges its presence  . . . . 

what do i need ?? drivers ?? m downloading drivers anyways . . . but there is no sign of the NVIDIA card even in 
ubuntu software center>>>edit>>software sources>>additional drivers

---

### Post by tad1073 on 2013-05-22
Is it on board or a card?

---

### Post by 3Miro on 2013-05-22
Laptop Nvidia graphics uses Optumus technology (i.e. the ability to switch between the integrated Intel and faster Nvidia). However, for several years Nvidia refused to support Optimus on Linux and even now, they don't support it on Ubuntu.

You can search around for people trying to enable partial support for Optimus via Bumblebee, but if I were in your shoes, I would just use the integrated Intel and doable Nvidia.

---

### Post by 3rdalbum on 2013-05-23
Is it turned off in the BIOS?

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Multimedia & Video**.*

---


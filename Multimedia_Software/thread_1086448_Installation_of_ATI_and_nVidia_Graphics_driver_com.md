---
title: "Installation of ATI and nVidia Graphics driver: command not found"
date: 2009-03-04
forum: Multimedia Software
---

### Post by sagramor on 2009-03-04
**running intrepid on hp dv6770se w/ geforce 8400m gs.**

i am following this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers)
but when i am in the virtual console and i run this command: 
```
http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installation_of_ATI_and_nVidia_Graphics_drivers
```
i get command not found. I googled this but couldn't find a solution. 

I am not sure if it is related, but i had to run this command to get my atheros going:
```
sudo aptitude install linux-backports-modules-intrepid-generic
```

any help is greatly appreciated.:-({|=

---

### Post by sagramor on 2009-03-04
d'oh! i had to change my permissions on the file. Solved.

---

### Post by kamssada on 2009-03-06
mine didn't work, i get a blank screen after boot... i had to fix the xserver using the recovery mode. still having issue, coz graphics card not installed...

---


---
title: "flash 10 wont work on ubuntu 8.04 ff 3.0.3"
date: 2009-03-27
forum: Multimedia Software
---

### Post by Intangir on 2009-03-27
i kept having a crash with flash9 when loading flash pages. i found out it was because ofa  sound bug, the recommended fix was upgrading to flash 10

so i installed it and installed it and installed it and it wouldnt work.. it kept saying i had flash 9 still

i deleted the flash9 .so file from every /usr/lib/mozilla, firefox, wherever else i could find it and replaced it with 10 in both the system wide and user specific directories

it didnt work

i gave up and installed ubuntu 8.10 on another partition and used my same home directory. fired up firefox and flash 10 worked without issue..

unfortunately xmms is gone and all my favorite game WoW runs at 10-20 fps slower and is extremely choppy, instead of getting 8-12 fps in terrible fights, i get 0.8 frames..

so i dont want to keep the upgrade. id rather use 8.04 cause everything is setup the way i like it and runs fine EXCEPT FOR flash 10

now when i boot 8.04 firefox claims flash 10 is installed! the pages i load up even set aside the space where flash should be, but it doesnt actually have the flash content there

about:plugins also shows that i have flash 10 installed fine

but it doesnt work.

im not even sure how its possible for 1 tiny addon to be such a humongous pain in the **** but it is..

i did some searching and found a couple threads with people saying they had the same problem, one random guy said he cleared it up but never explained how... thoughtful

anyone have any suggestions?

---

### Post by Intangir on 2009-03-27
i found out what was wrong

if you run into this issue you do:

ldd /usr/lib/adobe-flashplugin/libflashplayer.so

then if you see anything that says not found, you have to install those libraries

---

### Post by niteklub79 on 2009-03-28
how do you install the missing libraries?

---


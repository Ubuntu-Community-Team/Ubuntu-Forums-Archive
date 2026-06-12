---
title: "Envy problem"
date: 2008-09-30
forum: Multimedia Software
---

### Post by Chamillionaire2 on 2008-09-30
Hello,

ok i were trying to play wow on ubuntu and apprently i needed envy to config my vidoe drivers. but now that its installed my resoloutiopn is 800x somthing. how do i  unisntall envy and get my good res back?

my screen is a LCD one and i dont know what res it will do.

btw im using nvidia vidoe drivers.

Thanks Bye.

---

### Post by Chamillionaire2 on 2008-09-30
Ive found that in the hardware drivers app in system i use nivida driver, but it is not enabled. i enable it and restart as promoted, but then i get a Ubuntu is running in low graphics mode. and when i check to see if my nividi driver is still enabled. i find each time it has been un-enabled.

how can i fix this?

---

### Post by overdrank on 2008-09-30
Hi and you may try what is suggested here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

---

### Post by fourthofjuly on 2008-09-30
i guess you need to manually configure to get the desired resolution...

go to system > preferences > main menu > other (in left pane) > check screens and graphics (in right pane) - close

then from applications > other > screens and graphics, select your monitor and desired resolution

---

### Post by Chamillionaire2 on 2008-09-30
Both answer dident work im afriad. it came after i installed envy via terminal, i uninstalled envy ad the prbelm still continues.

Any other ideas?

---

### Post by Chamillionaire2 on 2008-09-30
Can anyone do remote assistence with me over pigin cus i dont know what to do and all the soloutions i found look very camplicated.

plus im new to ubuntu

---

### Post by easybake on 2008-09-30
> **Chamillionaire2 said:**
> Can anyone do remote assistence with me over pigin cus i dont know what to do and all the soloutions i found look very camplicated.

plus im new to ubuntu

I was running into a similiar problem do these in order.
```
sudo apt-get install envyng-gtk
```
when its finished in terminal run 
```
envyng-gtk
```
on the window prompt select the nvidia option and the second driver option not the latest one.
*restart if required*
Back in terminal run
```
nvidia-settings
```
you should be able to select the resolution there.

---

### Post by Chamillionaire2 on 2008-09-30
> **easybake said:**
> I was running into a similiar problem do these in order.
```
sudo apt-get install envyng-gtk
```
when its finished in terminal run 
```
envyng-gtk
```
on the window prompt select the nvidia option and the second driver option not the latest one.
*restart if required*
Back in terminal run
```
nvidia-settings
```
you should be able to select the resolution there.

THANKS Alot :) i read soloutions on the internet and looked very hard to do. but the simple explanation saved the day.

Thanks easybake

---


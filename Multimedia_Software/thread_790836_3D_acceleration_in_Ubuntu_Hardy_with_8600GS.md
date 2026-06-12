---
title: "3D acceleration in Ubuntu Hardy with 8600GS"
date: 2008-05-11
forum: Multimedia Software
---

### Post by jhetfield17 on 2008-05-11
Hi 
I tried to install the nvidia drivers with envy but it doesn't install 3D acceleration so I cant play Guild Wars with cedega.What can I do?

---

### Post by pro003 on 2008-05-11
try this:

```
sudo apt-get update
```

```
sudo apt-get install xserver-xgl
```

if it doesn't solve the problem just do everything pretty same but replace "install" with "remove"...

---

### Post by jhetfield17 on 2008-05-12
Nope didn't work.Still no luck.I even tried the last certified 8600 driver 100.14.03 but it throws an error when finishing the custom module build for my kernel.So I still can't have 3D.And the thing is that nvidia seems to have abandoned the 8600 series cause the last driver 169.something is for the 8700 series.


Any other suggestions??

---

### Post by jhetfield17 on 2008-05-12
I was running the cedega tests again and since I'm a little of a noob my self I came to realize that 3D acceleration is the same with the gears test and it measures performance but the gears test is perfect and it couldn't spin the gears any faster than that.So I'm guessing that my settings are wrong.

can anyone tell me what I need to change to make it work?

---

### Post by miguelssm on 2008-06-18
Well, you are very lucky, cause I can't have more than 800x600 resolution with my 8600 GS.
I've contact nVidia driver developers, and they said me that the bug will be solved in next driver; so, I'm waiting for a solution from nvidia itself.

I promise you a new post when everything would be OK.

Miguel (Spain)

__________

Visit [Fotos y Cosas]("http://www.fotosycosas.es").

---

### Post by miguelssm on 2008-08-11
Hi everyone:

NVidia has released the driver version 173.14.12 which includes support for 8600 GS.

[Follow this link.]("http://www.nvidia.com/object/linux_display_ia32_173.14.12.html")

I've not tested it yet, but...

Good luck!

---


---
title: "nvidia fan speed control"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by dubrict on 2006-09-18
Hi, I am running a dual-boot rig with 2 geforce 6600's in SLI, and I must say the fans on them get pretty loud.  In windows, I can use the program "rivatuner" to control the fan speeds so that when I'm not gaming, the fans spin a lot slower.. does anybody know any programs to do this in linux?  I've searched and turned up nothing.  Thanks

---

### Post by dubrict on 2006-12-03
I found a program, called nvclock.  It's available in the repositories.

in the terminal, run nvclock -f -F ##

where ## is the speed to set the fan, from 1 to 100%.
It's interesting, I set it to 98% and the amount of sound drastically reduces with no effect on the temperature.

---

### Post by miceagol on 2007-01-23
nvclock doesn't work with 8800GTS/GTX yet. Furthermore, nVidias own configuration program does only show the GPU temperature, but does not include any fan control. I'm going to ask nVidia to implement this when it's [possible to do so]("http://www.nvidia.com/object/feedback_temp.html"). I urge other Ubuntuers to do the same. :) More requests = Higher priority.

---


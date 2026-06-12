---
title: "WEIRD Nvidia problem"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by jaketoox on 2006-09-22
Hi everyone...
is there someone who can help....i have a VERY weird problem with my laptop (actually it is my girlfriend's laptop, Asus A6TC)...I have installed Nvidia drivers ( NVIDIA-Linux-x86_64-1.0-8762-pkg2.run) and  the problem is that the drivers will not load at startup....it says that "x is not configured, and start again after it is configured properly"...so i have to login from command line....and the weird part is this: i start the nvidia-installer (sudo sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run) and when it asks, if i want to install, i cancel it...after that i do (sudo /etc/init.d/gdm restart).....and...believe or not...Nvidia logo appears and gdm starts and i can do normal login, and everything works fine...till next time i boot my laptop....start installer,cancel it,restart gdm,login again,be happy with your laptop.....it is REALLY annoying....help is needed...](*,) ](*,)

---

### Post by tseliot on 2006-09-22
> **jaketoox said:**
> Hi everyone...
is there someone who can help....i have a VERY weird problem with my laptop (actually it is my girlfriend's laptop, Asus A6TC)...I have installed Nvidia drivers ( NVIDIA-Linux-x86_64-1.0-8762-pkg2.run) and  the problem is that the drivers will not load at startup....it says that "x is not configured, and start again after it is configured properly"...so i have to login from command line....and the weird part is this: i start the nvidia-installer (sudo sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run) and when it asks, if i want to install, i cancel it...after that i do (sudo /etc/init.d/gdm restart).....and...believe or not...Nvidia logo appears and gdm starts and i can do normal login, and everything works fine...till next time i boot my laptop....start installer,cancel it,restart gdm,login again,be happy with your laptop.....it is REALLY annoying....help is needed...](*,) ](*,)
try envy:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

install it, launch it and select the "uninstall" function and then the "install" function.

That should clean the mess ;)

---

### Post by jaketoox on 2006-09-22
[size="7"]GRRRRRRRRRREAT!!!![/size]

If i were a gay i would KISS you...(suppose i'm not:rolleyes: )...anyway..very big thanks to you, tseliot, now my girlfriend will not kill me because of :oops: destroying her new laptop....

---


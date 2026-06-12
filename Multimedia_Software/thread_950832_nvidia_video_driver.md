---
title: "nvidia video driver"
date: 2008-10-17
forum: Multimedia Software
---

### Post by linuxnoob40 on 2008-10-17
after the last update i lost my video driver and have been unable to reinstall it. envy is no help and i have no propriatry drivers in use in the system. 
i have tried to follow the guides but i guess i just dont comprehend or i have the memory span of a fish. please help me...

---

### Post by randolf_carter on 2008-10-17
Hi,try this:

1- Log in console ALT+F1
2- Exec:

wget [http://es.download.nvidia.com/XFree86/Linux-x86_64/177.80/NVIDIA-Linux-x86_64-177.80-pkg2.run](http://es.download.nvidia.com/XFree86/Linux-x86_64/177.80/NVIDIA-Linux-x86_64-177.80-pkg2.run) (GFORCE 7,8,9. For other version say it)

3- chmod NVIDIA-Linux-x86_64-177.80-pkg2.run
4- ./NVIDIA-Linux-x86_64-177.80-pkg2.run
5- Try to follow the indications.
6- Edit:
 nano /etc/X11/xorg.conf
7-Try to find the section:

"Section "Device"
    Identifier     "nVidia Corporation GeForce 6500"
    Driver         "nv"
EndSection"

And change:

"Section "Device"
    Identifier     "nVidia Corporation GeForce 6500"
    Driver         "nvidia"
EndSection

8- Save changes /CTRL+x) and shutdown -r -y now

I wish you lucky





> **linuxnoob40 said:**
> after the last update i lost my video driver and have been unable to reinstall it. envy is no help and i have no propriatry drivers in use in the system. 
i have tried to follow the guides but i guess i just dont comprehend or i have the memory span of a fish. please help me...

---

### Post by linuxnoob40 on 2008-10-17
Hi,try this:

> 1- Log in console ALT+F1
2- Exec:

wget [http://es.download.nvidia.com/XFree8...77.80-pkg2.run](http://es.download.nvidia.com/XFree8...77.80-pkg2.run) (GFORCE 7,8,9. For other version say it)


this is what i got. ???


 [http://es.download.nvidia.com/XFree8...77.80-pkg2.run](http://es.download.nvidia.com/XFree8...77.80-pkg2.run)
           => `XFree8...77.80-pkg2.run'
Resolving es.download.nvidia.com... 74.128.17.242, 74.128.17.243
Connecting to es.download.nvidia.com|74.128.17.242|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
15:21:12 ERROR 404: Not Found.

---


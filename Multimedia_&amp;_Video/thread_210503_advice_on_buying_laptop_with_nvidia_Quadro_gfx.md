---
title: "advice on buying laptop with nvidia Quadro gfx"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by syxbit on 2006-07-07
i have a dell e1505 laptop with an ATI x1400 gfx card
i'm frankly fed up with drivers. They just plain suck
i manually installed the latest ones, but my dvd playback sucks.
i'm looking at getting the Dell Latitude D620
it has Quadro NVS 110.
anyone know what driver support is like in Ubuntu? (cause it's not a normal nvidia card, it's their workstation card)
i'd really appreciate the help, as linux support is a must for me to buy a laptop

---

### Post by 5-HT on 2006-07-07
That card is fully supported by the Nvidia binary drivers (needed for 3d accel) available in Dapper's repos and will work with the opensource 'nv' drivers.
There are a few great guides on installing Nvidia's drivers floating around these forums.

In a nutshell:
Download and install the driver (you will need the appropriate 'restricted-modules' for your kernel which are installed by default)
```
sudo apt-get install nvidia-glx
``` 
Automagically configure your xorg.conf
```
 sudo nvidia-xconfig 
``` 
Restart X, or reboot.

To get to the Nvidia's settings app either enter 'nvidia-settings' in a terminal or make a shortcut.

Hope that helps and enjoy the new notebook if you get it!

---


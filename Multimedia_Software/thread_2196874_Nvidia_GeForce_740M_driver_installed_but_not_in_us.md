---
title: "Nvidia GeForce 740M driver installed but not in use"
date: 2013-12-31
forum: Multimedia Software
---

### Post by awhb87 on 2013-12-31
I'm on an HP Envy 15 laptop that has two graphics cards. One is the standard Intel card, and the other is my Nividia GeForce 740M. I recently got the nvidia-current drivers for my laptop, and that worked, but when I launch my Nividia X Server settings program I get the following:

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

So, naturally, I ran the: sudo nvidia-xconfig

Well that hasn't helped me so far. Any help would be greatly appreciated.

---

### Post by Bashing-om on 2014-01-01
awhb87; Hi !

an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See this link here for installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)

Ubuntu version 13.10 does have increased support for the switchable drivers> Else also look at:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10)

Older releses benefit from BumbleBee :
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

[INDENT][INDENT]Just try'n to help
[/INDENT][/INDENT]

---

### Post by awhb87 on 2014-01-01
I appreciate the advice Bashing-om, but I ran into some problems with bumblebee. I can run optirun glxspheres, but as soon as I try primusrun glxspheres, i get the following:

```
andrew@Hennessy-Linux:~$ primusrun glxspheres 
Polygons in scene: 62464
Visual ID of window: 0xfc
Segmentation fault (core dumped)

```

Just some extra info in case it's helpful; I'm running my grub in nomodeset, and I'm running the nvidia-331 open drivers. 

Any help would be appreciated.

---

### Post by Bashing-om on 2014-01-01
awhb87; Hey,

Regret to say "primusrun" is out of my sphere of knowledge. Others will have to advise further.

[INDENT][INDENT]What I do not know fills a very large partition
[/INDENT][/INDENT]

---


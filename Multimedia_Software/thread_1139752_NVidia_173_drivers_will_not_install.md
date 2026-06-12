---
title: "NVidia 173 drivers will not install"
date: 2009-04-27
forum: Multimedia Software
---

### Post by dbaldaro on 2009-04-27
I have just upgraded to 9.04 and my legacy NVidia FX 500/FX 600 card is not working properly. I can start ubuntu using the generic drivers - but the NVIDIA 173 drivers refuse to install. 

If I download the latest 173.14.18 from NVidia's website and run
> david@george:~$ sudo sh NVIDIA-Linux-x86-173.14.18-pkg1.run

it bombs saying that it cannot compile the drivers because it is "unable to find the kernel source tree for the running kernel. 

> david@george:~$ uname -a
Linux george 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux

I have installed the linux-headers and linux-source packages but cannot get the NVIDIA 173 drivers to install and load.

Any ideas, please anyone?

---

### Post by NT4usB on 2009-04-27
iirc, you need to have the kernel source (and other stuff) installed before you can build these things. They're in the repositories but I'm not really sure what they're called or what all you need.

Try Envy? It's in the repositories... It handles the source stuff for you.

---


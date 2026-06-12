---
title: "Installing Nvidia drivers"
date: 2009-02-16
forum: Multimedia Software
---

### Post by kerryhall on 2009-02-16
I need some help installing Nvidia graphics drivers on Intrepid Ibex. I tried downloading and installing the 180.23 drivers from Nvidia's web site, but I got a message saying that the kernel module failed to initialize. I have also tried the 180 drivers in the restricted drivers section, and I got an error saying that my settings could not be detected and would have to be configured manually. I have run nvidia-xconfig in both cases.

I have no idea what is going on.

Thanks!

---

### Post by itang sanjana on 2009-02-16
Hello, I just follow this step by step instruction with no problem.
Hope this helps.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Cheers ..

---

### Post by norwoods on 2009-02-16
Anders Kaseorg has built packages for Jaunty that will also work in Intrepid. They are available in his ppa here:
[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

---

### Post by kerryhall on 2009-02-16
Thanks to both of you!

I finally got things working. I had to install the restricted modules, uninstall the Nvidia driver, use apt to get the 180 driver because it wasn't showing up in the hardware drivers, then install that driver, now FINALLY it works! This solves my DRI problem too!

---

### Post by kerryhall on 2009-02-18
Ok, now the drivers still appear to be installed, but I am randomly back to having no direct rendering. I have not altered my system in any way besides installing a few dev packages. I tried disabling then reenabling the drivers, with no luck.

Any idea what's going on?

---

### Post by kerryhall on 2009-02-18
I hate to bump this so soon, but without video drivers, I'm basically dead in the water.

---

### Post by kerryhall on 2009-02-20
Bump. :(

---

### Post by norwoods on 2009-02-20
i cannot say i have a clue but i updated to 8.10 because the video driver support seems to be more available.

---

### Post by kerryhall on 2009-02-21
Thanks, I am using 8.10.

I have tried enabling and disabling various available drivers, with no luck. Anyone have any ideas?? I am seriously considering wiping my hard drive and going with a clean slate at this point, something I really would not like to do.

I started with Gutsy on this machine, I believe, and have been upgrading since.

There seems to be a bug in the hardware drivers manager. Why does it say the driver is enabled when it clearly is not?

---

### Post by norwoods on 2009-02-21
after i recently upgraded from 180.27 to 180.29 with synaptic, i was still running 180.27 until i deactivated the 180 driver and then activated the 180 driver in the System--Administration--Hardware Drivers application.

what driver does your NVIDIA X server setting say is running.

---

### Post by kerryhall on 2009-03-03
Hmm, it says 180.11. 180.27 and 180.29 aren't available for some reason, synaptic only shows 180.11 as being available.

How do I get 180.29?

---

### Post by kerryhall on 2009-03-04
Bump.

---

### Post by norwoods on 2009-03-04
again, Anders Kaseorg has built packages for Jaunty that will also work in Intrepid. They are available in his ppa here:
[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

---

### Post by kerryhall on 2009-03-05
Thank you, I have tried these packages with no success. It shows driver 180.29 as being enabled, but direct rendering is still not enabled.

---

### Post by turshu on 2009-03-06
You can use this post here. It works well for me and it seems everything running ok even direct rendering 

[http://samet.kilictas.com/how-to-ins...n-your-ubuntu/](http://samet.kilictas.com/how-to-ins...n-your-ubuntu/)

---

### Post by norwoods on 2009-03-06
i download the latest releases, 180.37 currently, from [www.avenard.org](www.avenard.org).
i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by kerryhall on 2009-04-23
Oh man, so here is the problem that I was having, I finally solved it by going on the IRC channel. Basically, I had tried to compile my own version of Mesa, just as a learning experience. I had installed it, but forgot to uninstall it. This was seriously screwing things up. Now DRI and everything is working perfectly. Thanks to everyone for their help!

---


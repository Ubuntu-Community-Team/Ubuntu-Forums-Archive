---
title: "install newest nvidia driver in ubuntu server"
date: 2009-08-31
forum: Multimedia Software
---

### Post by pythonscript on 2009-08-31
I installed a command line only ubuntu with icewm as the window manager, and now I'm looking to install the latest nvidia driver from their website. I'm using this driver as opposed to the ones in the repositories because I'm running a server kernel on my laptop and those drivers don't support it. When my laptop boots, I manually start the x server with startx, and it works just fine.

So, I go to install the latest driver, download it, and run

```
sudo sh NVIDIA-Linux-x86-*version goes here*.run
``` but after I move through some of the command line accept dialogs, I get a message that nvidia could not find a precompiled source package for my kernel (2.6.28-15 server) and tries to download them. Then... it says it's missing them and the installation says failed and quits. Any ideas? Sorry about the long thread, but I'd really like to get this working so I can actually watch movies on here without a really low refresh rate. Thanks!

---

### Post by Shazaam on 2009-09-01
Try this...
Open terminal, enter-
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by pythonscript on 2009-09-05
That solved the problem. Thanks!

---


---
title: "Resolution Problems 8600gt"
date: 2008-05-22
forum: Multimedia Software
---

### Post by TR13 on 2008-05-22
Hi, 

My Computer
Core2, XFX 8600GT, 19" LCD, ASUS P5N-E SLI, Ubuntu 7.4

My Problem
After installing Ubuntu i could not get the correct resolution (1400x900). I tried installing the Driver for the graphics card from the synaptic manager, but when i restart the computer the x server stops working and i have to reconfigure it. I tried downloading the driver from nvidia.com and i got a NVIDIA-Linux-x86-169.12-pkg1.run. But i don't know how to use it. I also tried installing the restricted driver but it says that my hardware does not require a restricted driver.. Please help....

---

### Post by whis on 2008-05-22
I had the same problem (also with 8600GT). I ended up installing Envy (i think with apt-get). Envy installs the driver for you:)

---

### Post by TR13 on 2008-05-22
Thanks anyways... i upgraded to Gutsy and that solved the problem....

---

### Post by Xiong Chiamiov on 2008-05-22
> **TR13 said:**
> Thanks anyways... i upgraded to Gutsy and that solved the problem....
From Hardy?

The NVIDIA drivers in the repos have a problem with the kernel in Hardy.  You can fix it [like this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

---


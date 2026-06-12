---
title: "Nvidia driver wont install!!"
date: 2009-01-23
forum: Multimedia Software
---

### Post by Wanas on 2009-01-23
I tried to install the nvidia driver 177 via the synaptic manager but it when I loged in the xorg wont load and told me if I want to reconfigure the xorg or restore it so I chosen to restore, 

I then tried to download the Nvidia 180 beta driver from here [ftp://download.nvidia.com/XFree86/Linux-x86_64/180.22/NVIDIA-Linux-x86_64-180.22-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.22/NVIDIA-Linux-x86_64-180.22-pkg1.run)
Then when I tried to install it manually I have this message:

Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.

Edit: I am using Ubuntu 8.10 64bit 
I was using Ubunut 8.10 32bit before and the beta driver works for me fine

---

### Post by Therion on 2009-01-23
See this thread:  [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by Wanas on 2009-01-23
I tried what he said in this thread but I have the above message 
What to do with it?

---

### Post by alkamid on 2009-02-18
Get headers for your kernel
```
sudo apt-get install linux-headers
```

---


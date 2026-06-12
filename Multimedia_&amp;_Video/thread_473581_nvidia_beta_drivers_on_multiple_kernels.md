---
title: "nvidia beta drivers on multiple kernels"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by martinico on 2007-06-14
Hello,

I have successfully installed the nvidia beta drivers for my 8600 gts graphic card on Feisty, with the method of this post :
[http://ubuntuforums.org/showthread.php?t=460765](http://ubuntuforums.org/showthread.php?t=460765)

(in short, prepare the install with module-assistant (m-a), shut down X server, and run the nividia executable).

I think it should be possible to install these drivers for my other kernels too, but because I'm a newbie, I would like to know the opinion of more advanced users ;) , before I try.

I read the doc of module-assistant and of nvidia installer ("man m-a", and "nvidia-installer --advanced-options" or "sh NVIDIA-Linux-x86-100.14.06-pkg1.run --advanced-options")

For module-assistant, it is said that it is possible to specify another kernel that the current one with the option --kernel-dir.

For the nvidia-installer, it is said that it is possible to build and install the driver on a non-running kernel with the option --kernel-name=KERNEL-NAME ,
and to install a kernel module only, and do not uninstall the existing driver, with the option --kernel-module-only.

Ok, so what I project to do is (with sudo privileges), on a non-running kernel :

```
m-a --kernel-dir /usr/src/kernel-headers-EXACTNAME update
m-a --kernel-dir /usr/src/kernel-headers-EXACTNAME prepare
m-a --kernel-dir /usr/src/kernel-headers-EXACTNAME auto-install nvidia

nvidia-installer --kernel-name=kernel-headers-EXACTNAME --kernel-module-only
```

Please, let me know what do you think about that before I try and break my current installation ;) .

---


---
title: "nvidia kernel module 2.6.15.26"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by bastiegast on 2006-08-31
Hi,

This problem is driving me nuts. Whenever I try to enable 3d acceleration for my nvidia card, my x server complains he cant find the nvidia kernel module. Now im suspecting this is because the kernel im running on is 2.6.15.26 and the nvidia-glx and restricted modules ive installed are 2.6.15.11 or 2.6.15.23. And somehow I cant find the packages with the right version in synaptic. As far as i know I enabled the right repositories. Maybe someone can tell me how to savely downgrade my kernel or give me the repositories i need.

---

### Post by tseliot on 2006-08-31
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

NOTE: it's ` and not '

See if that solves the problem.

---

### Post by bastiegast on 2006-08-31
Already tried that and it couldnt find the package.

btw i just found that my older kernels where still in the /boot folder so i modified grub to boot the older kernel and it WORKED :P
however im running on an older kernel now (2.6.15-23 instead of 2.6.15-26).

---

### Post by tseliot on 2006-08-31
A suggestion:
Make sure you install also the restricted modules for every new kernel you decide to install (or if it's updated): 
```
sudo apt-get install linux-386
```

Or you can put "686", "k7", etc. instead of "386", according to your architecture, which you can check out by typing: 
```
uname -r
```

After you do that the restricted modules will be installed every time your kernel is updated (unless you install a kernel for a different architecture, e.g. you have a 386 kernel and install a 686 kernel).

---

### Post by bastiegast on 2006-08-31
Thank you for your help, got it working :)

---


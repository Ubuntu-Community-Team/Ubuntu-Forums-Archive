---
title: "X doesn't starts in the last kernel update"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by kirbyboy on 2007-06-29
Hi, my english is not very good, so, i hope somebody understand what i'm trying to say.

I use Feisty Fawn and with the first kernel, i think it was the 2.6.20.15(i'm not in my computer now), i installed my nvidia(GeForce FX 5500) throught restricte manager and worked without problems.  Some day, the system updated the kernel to 2.6.20.16(i think), and some modules of the kernel with restricted manager too, i tested the new kernel version and the X could start without problems too, but i decided to use the old kernel.  The fact is than some time ago, trought restrited manager i uninstalled the nvidia driver and reinstalled again and today, accidentally, i choose the new kernel to start, but the X could not start.  Is there some way the Graphics card works in all the kernels?, thanks.

---

### Post by ianthewarrior on 2007-06-29
i got same problem here. i have the same display card too.
i dont know why, but it seems that it cannot load nvidia.ko
i try to make symlink
sudo ln -s /lib/modules/2.6.20-16-generic/nvidia/nvidia.ko /lib/modules/2.6.20-16-generic/volatile/
but the new problem came. every restart, i cannot load anymore, so i have to make symlink again.
anyone please help.....

---

### Post by kirbyboy on 2007-06-29
if i make the symlink, will i be able to run the old kernel without problems like now?

---

### Post by tseliot on 2007-06-29
try with:
```
sudo apt-get install linux-restricted-modules`uname -r`
```

and
```
sudo depmod -ae
```

---

### Post by kirbyboy on 2007-06-29
Hi, when i started my computer this night in the old kernel, automatically installed the new restricted modules for new kernel and nvidia-glx(i think this is the name), i think it was installed because this morning i used the new kernel and the X could not start(i suposse), now i'm writing from my new kernel working.  I'll save this code for future.  Thanks for your help.

---

### Post by wilialm on 2007-07-01
I have got the same problem. I used ENVY to install the latest Nvidia drivers for my graphics card NVIDIA 8500 GT but X will only start with kernal 2.6.20-15, it will not start with the latest kernal 2.6.20-16. I am sure it will be fixed soon.:D

---

### Post by kirbyboy on 2007-07-02
When i uses Ubuntu 6.10 and ENVY, that's was normal, what i did:
I run the new kernel, run ENVY, and uninstall and install the nvidia card(it was about 10 seconds), and the new kernel could start the X, the problem was that you could not start X with old kernels.  With restricted-manager, you can run each kernel, and the X works without problems.

---


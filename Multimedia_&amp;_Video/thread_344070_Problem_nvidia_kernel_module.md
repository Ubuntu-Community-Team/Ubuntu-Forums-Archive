---
title: "Problem nvidia kernel module"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by MatheO on 2007-01-22
Hello everybody !

sorry for my english, i come from Belgium and generally, I speak french. :)

This morning, i've run my computer with Kubuntu edgy like every morning and all was normal. But after a update from adept, i restarded my computer and the X server don't want to launch with this message :
```

 FATAL : could not open /lib/modules/2.6.17-10-generic/volatile/nvidia.ko. 
No such file or directory

EE : NVIDIA (0): failed to load the nvidia-kernel module
EE : NVIDIA (0): ***Abording***
EE : Screen(s) found, but none have a usable configuration
```

I only can use a console (terminal) (no graphical mode)

do you have some ideas to help me ? a solution for my problem ?

Ive a Nvidia Geforce 6800 :)

Thankx !

---

### Post by chrisccoulson on 2007-01-22
On my machine, that folder is mounted as a temporary filesystem. Can you post the output of:

```
cat /etc/mtab
```

I think it should contain a line like this:

```
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
```

If that line is there, then try reinstalling the nvidia-glx and linux-restricted-modules packages from the repositories (assuming that this is how you installed the NVIDIA drivers in the first place)

---


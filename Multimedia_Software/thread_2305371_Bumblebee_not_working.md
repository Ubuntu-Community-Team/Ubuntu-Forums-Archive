---
title: "Bumblebee not working"
date: 2015-12-05
forum: Multimedia Software
---

### Post by marek16 on 2015-12-05
I have a fresh isntallation of Kubuntu 15.10 on my laptop and now I tried to install bumblebee with this command:

```
sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic
```

When I am trying to run something via optirun I am getting this error:
```
[  857.699769] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[  857.699837] [ERROR]Aborting because fallback start is disabled.
```

I tried also this solution found on ubuntu forums, but did not helped for me:
> change 

Driver= 
   to    
Driver=nvidia

and

KernelDriver=nvidia-current 
to    
KernelDriver=nvidia

How to fix this issue ?
I have this nvidia driver installed:
[http://s16.postimg.org/hsorbxv8l/snapshot1.png](http://s16.postimg.org/hsorbxv8l/snapshot1.png)

---

### Post by marek16 on 2015-12-05
I also tried to follow this guide, but I am still getting the same error:

[http://unix.stackexchange.com/questions/243535/how-to-make-nvidia-optimus-work-on-kubuntu-15-10](http://unix.stackexchange.com/questions/243535/how-to-make-nvidia-optimus-work-on-kubuntu-15-10)

---


---
title: "error of &quot;build-essential linux-headers&quot; and &quot;make&quot; when installing driver"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by Yifan_Wang on 2013-09-01
[http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332)   I was following this article to try to get my killer E2200 ethernet work. But when I input ```
sudo apt-get install build-essential linux-headers
``` there was some error that says```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-3.2.0-49-lowlatency 3.2.0-49.51
  linux-headers-3.8.0-26-generic 3.8.0-26.38~precise2
  linux-headers-3.8.0-25-generic 3.8.0-25.37~precise1
  linux-headers-3.2.0-49-virtual 3.2.0-49.75
  linux-headers-3.2.0-49-generic 3.2.0-49.75
  linux-headers-3.2.0-49 3.2.0-49.75
  linux-headers-3.2.0-30-virtual 3.2.0-30.48
  linux-headers-3.2.0-30-generic 3.2.0-30.48
  linux-headers-3.2.0-30 3.2.0-30.48
  linux-headers-3.2.0-24-virtual 3.2.0-24.39
  linux-headers-3.2.0-24-generic 3.2.0-24.39
  linux-headers-3.2.0-24 3.2.0-24.39
  linux-headers-3.2.0-52-lowlatency 3.2.0-52.54
  linux-headers-3.2.0-51-lowlatency 3.2.0-51.53
  linux-headers-3.2.0-48-lowlatency 3.2.0-48.50
  linux-headers-3.2.0-44-lowlatency 3.2.0-44.48
  linux-headers-3.2.0-41-lowlatency 3.2.0-41.45
  linux-headers-3.2.0-40-lowlatency 3.2.0-40.43
  linux-headers-3.2.0-39-lowlatency 3.2.0-39.41
  linux-headers-3.2.0-38-lowlatency 3.2.0-38.40
  linux-headers-3.2.0-37-lowlatency 3.2.0-37.37
  linux-headers-3.2.0-36-lowlatency 3.2.0-36.36
  linux-headers-3.2.0-35-lowlatency 3.2.0-35.34
  linux-headers-3.2.0-33-lowlatency 3.2.0-33.33
  linux-headers-3.8.0-29-generic 3.8.0-29.42~precise1
  linux-headers-3.8.0-27-generic 3.8.0-27.40~precise3
  linux-headers-3.8.0-23-generic 3.8.0-23.34~precise1
  linux-headers-3.8.0-22-generic 3.8.0-22.33~precise1
  linux-headers-3.8.0-21-generic 3.8.0-21.32~precise1
  linux-headers-3.8.0-19-generic 3.8.0-19.30~precise1
  linux-headers-3.2.0-52-virtual 3.2.0-52.78
  linux-headers-3.2.0-52-generic 3.2.0-52.78
  linux-headers-3.2.0-52 3.2.0-52.78
  linux-headers-3.2.0-51-virtual 3.2.0-51.77
  linux-headers-3.2.0-51-generic 3.2.0-51.77
  linux-headers-3.2.0-51 3.2.0-51.77
  linux-headers-3.2.0-48-virtual 3.2.0-48.74
  linux-headers-3.2.0-48-generic 3.2.0-48.74
  linux-headers-3.2.0-48 3.2.0-48.74
  linux-headers-3.2.0-45-virtual 3.2.0-45.70
  linux-headers-3.2.0-45-generic 3.2.0-45.70
  linux-headers-3.2.0-45 3.2.0-45.70
  linux-headers-3.2.0-44-virtual 3.2.0-44.69
  linux-headers-3.2.0-44-generic 3.2.0-44.69
  linux-headers-3.2.0-44 3.2.0-44.69
  linux-headers-3.2.0-43-virtual 3.2.0-43.68
  linux-headers-3.2.0-43-generic 3.2.0-43.68
  linux-headers-3.2.0-43 3.2.0-43.68
  linux-headers-3.2.0-41-virtual 3.2.0-41.66
  linux-headers-3.2.0-41-generic 3.2.0-41.66
  linux-headers-3.2.0-41 3.2.0-41.66
  linux-headers-3.2.0-40-virtual 3.2.0-40.64
  linux-headers-3.2.0-40-generic 3.2.0-40.64
  linux-headers-3.2.0-40 3.2.0-40.64
  linux-headers-3.2.0-39-virtual 3.2.0-39.62
  linux-headers-3.2.0-39-generic 3.2.0-39.62
  linux-headers-3.2.0-39 3.2.0-39.62
  linux-headers-3.2.0-38-virtual 3.2.0-38.61
  linux-headers-3.2.0-38-generic 3.2.0-38.61
  linux-headers-3.2.0-38 3.2.0-38.61
  linux-headers-3.2.0-37-virtual 3.2.0-37.58
  linux-headers-3.2.0-37-generic 3.2.0-37.58
  linux-headers-3.2.0-37 3.2.0-37.58
  linux-headers-3.2.0-36-virtual 3.2.0-36.57
  linux-headers-3.2.0-36-generic 3.2.0-36.57
  linux-headers-3.2.0-36 3.2.0-36.57
  linux-headers-3.2.0-35-virtual 3.2.0-35.55
  linux-headers-3.2.0-35-generic 3.2.0-35.55
  linux-headers-3.2.0-35 3.2.0-35.55
  linux-headers-3.2.0-34-virtual 3.2.0-34.53
  linux-headers-3.2.0-34-generic 3.2.0-34.53
  linux-headers-3.2.0-34 3.2.0-34.53
  linux-headers-3.2.0-33-virtual 3.2.0-33.52
  linux-headers-3.2.0-33-generic 3.2.0-33.52
  linux-headers-3.2.0-33 3.2.0-33.52
  linux-headers-3.2.0-32-virtual 3.2.0-32.51
  linux-headers-3.2.0-32-generic 3.2.0-32.51
  linux-headers-3.2.0-32 3.2.0-32.51
  linux-headers-3.2.0-31-virtual 3.2.0-31.50
  linux-headers-3.2.0-31-generic 3.2.0-31.50
  linux-headers-3.2.0-31 3.2.0-31.50
  linux-headers-3.2.0-29-virtual 3.2.0-29.46
  linux-headers-3.2.0-29-generic 3.2.0-29.46
  linux-headers-3.2.0-29 3.2.0-29.46
  linux-headers-3.2.0-27-virtual 3.2.0-27.43
  linux-headers-3.2.0-27-generic 3.2.0-27.43
  linux-headers-3.2.0-27 3.2.0-27.43
  linux-headers-3.2.0-26-virtual 3.2.0-26.41
  linux-headers-3.2.0-26-generic 3.2.0-26.41
  linux-headers-3.2.0-26 3.2.0-26.41
  linux-headers-3.2.0-25-virtual 3.2.0-25.40
  linux-headers-3.2.0-25-generic 3.2.0-25.40
  linux-headers-3.2.0-25 3.2.0-25.40
  linux-headers-3.2.0-23-lowlatency 3.2.0-23.31
  linux-headers-3.2.0-23-virtual 3.2.0-23.36
  linux-headers-3.2.0-23-generic 3.2.0-23.36
  linux-headers-3.2.0-23 3.2.0-23.36
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate


```
Then form some other article on Internet adressing the build-essential linux-headers I tried this:```
sudo apt-get install build-essential linux-headers-$(uname -r)


``` and I got this:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.8.0-29-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
``` So I assumed maybe I already installed those packages and moved on to next steps. But when I run "make" there was another error:```
make -C /lib/modules/3.8.0-29-generic/build M=/home/wyf95419/Desktop/compat-wireless-2012-05-10-p modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
  CC [M]  /home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.o
In file included from /home/wyf95419/Desktop/compat-wireless-2012-05-10-p/include/linux/bcma/bcma.h:8:0,
                 from /home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/bcma_private.h:8,
                 from /home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.c:8:
/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/include/linux/bcma/bcma_driver_pci.h:207:23: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bcma_core_pci_init’
In file included from /home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.c:8:0:
/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/bcma_private.h:16:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bcma_bus_register’
/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.c:142:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘bcma_bus_register’
/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.c:17:21: warning: ‘bcma_bus_next_num’ defined but not used [-Wunused-variable]
/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.c:86:12: warning: ‘bcma_register_cores’ defined but not used [-Wunused-function]
make[3]: *** [/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma/main.o] Error 1
make[2]: *** [/home/wyf95419/Desktop/compat-wireless-2012-05-10-p/drivers/bcma] Error 2
make[1]: *** [_module_/home/wyf95419/Desktop/compat-wireless-2012-05-10-p] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'
make: *** [modules] Error 2


```
So I am totally confused right now...

---

### Post by TheFu on 2013-09-01
To me, it looks like there is a flaw in  bcma_driver_pci.h at line 207. Did you contact the developer of the driver?

---

### Post by steeldriver on 2013-09-01
Isn't a compat-wireless from 2012-05-10 going to be way out of date? anything backported in 2012 probably comes from an older kernel than you're already running (3.8.0.xx), and may not even be build-compatible

---

### Post by varunendra on 2013-09-01
Those make errors should be easy to fix with something like step #3 in this post : [http://ubuntuforums.org/showthread.php?t=2169602&p=12770984#post12770984](http://ubuntuforums.org/showthread.php?t=2169602&p=12770984#post12770984) , but I totally agree with what steeldriver said -
> **steeldriver said:**
> Isn't a compat-wireless from 2012-05-10 going to be way out of date? anything backported in 2012 probably comes from an older kernel than you're already running (3.8.0.xx), and may not even be build-compatible

As such, I think you should start a new thread for your wireless problem instead of following one that offers an outdated solution. If you concur with us and start a new one, please post a link to it here so we can follow.

---

### Post by Yifan_Wang on 2013-09-01
I'm pretty sure the problem is not the driver because there are plenty of people following the same instructions and getting their problems solved. And I kinda remember some days ago when I tried to use "make" for something else there seemed to be a same kind of problem. So I guess the problem may be something with my system configuration.

---

### Post by Yifan_Wang on 2013-09-01
But in the thread I mentioned there are a lot of people who successfully installed the driver recently. I guess the problem may come from my system configuration.

---

### Post by Yifan_Wang on 2013-09-01
Guys I got the problem solved! There is a newer version of the driver and I tried that and it totally worked out! Thank you all for your answers!

---

### Post by varunendra on 2013-09-01
> **Yifan_Wang said:**
> I'm pretty sure the problem is not the driver because there are plenty of people following the same instructions and getting their problems solved. And I kinda remember some days ago when I tried to use "make" for something else there seemed to be a same kind of problem. So I guess the problem may be something with my system configuration.
Not configuration, it is the kernel.
There have been some critical changes introduced in kernel version 3.4-rc1~54 and later. It seems a few more things have been dropped in version 3.8 onwards.
The "*expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before....*" error is a result of that. The older driver source files use some codes that are no longer supported by the newer kernels. I bet all those whose problems were 'Solved' with the same solution (without required new patches) must have been using older kernels.

> **Yifan_Wang said:**
> Guys I got the problem solved! There is a newer version of the driver and I tried that and it totally worked out! Thank you all for your answers!

Congrats !
I'm sure a link to the working driver would be much appreciated. :)

---

### Post by Bucky Ball on 2013-09-02
*Thread moved to **Networking & Wireless**.*

---

### Post by Yifan_Wang on 2013-09-02
Here: [http://ubuntuforums.org/showthread.php?t=2008332&page=7](http://ubuntuforums.org/showthread.php?t=2008332&page=7)   post#61&63

---


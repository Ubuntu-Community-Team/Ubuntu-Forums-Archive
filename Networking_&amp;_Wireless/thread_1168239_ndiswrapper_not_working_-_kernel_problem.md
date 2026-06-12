---
title: "ndiswrapper not working - kernel problem?"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by 4dplane on 2009-05-23
Hi, I am ubuntu 9.04 with kernel version 2.6.29-02062903-generic. I have tried to install many wireless USB cards and I am always getting the same error.

first I installed ndiswrapper-common, ndiswrapper-utils-1.9 and ndisgtk. I then run ndisgtk and load the windows driver. I am currently trying my d-link DWA-142. When I select the driver on anycard I have tried I get this error:
```

Module could not be loaded. Error was:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
**FATAL: Module ndiswrapper not found.**

Is the ndiswrapper module installed?
```


I believe the problem is with my Kernel. I have updated it and when I type locate ndiswrapper I get among many things:

```
/lib/modules/2.6.27-11-generic/kernel/ubuntu/ndiswrapper
/lib/modules/2.6.27-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper
/lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
```

It appears the wrapper is not set for my current Kernel. I have read things that sujest this is the problem but I do not know how to fix it.

Here is my lsusb:

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3b10 D-Link System RangeBooster N Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 047d:1005 Kensington TurboBall
Bus 005 Device 002: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Thanks,
4dplane

---

### Post by 67GTA on 2009-05-23
You need to reboot for the module to be loaded, or load it manually with ```
sudo modprobe ndiswrapper
``` in a terminal. You can check if it is loaded with ```
lsmod
``` in a terminal. If for some reason it doesn't survive a reboot, you can add it to /etc/modules. Open a terminal and run ```
gksudo gedit /etc/modules
``` Then add ```
ndiswrapper
``` to the end of the file. This file will be read at each boot and load modules listed here.

---

### Post by 4dplane on 2009-05-23
Thanks for the input but the problem is still there.

I added the ndiswrapper to /etc/modules and rebooted.

I then type lsmod and there is no ndiswrapper mod running.

I then type: modprobe ndiswrapper and I get this error:

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
```


Thanks,
4d

---

### Post by 67GTA on 2009-05-23
Try these three commands:

```
sudo ndiswrapper -m

sudo ndiswrapper -ma

sudo ndiswrapper -mi
```

Then try modprobe again.

---

### Post by 4dplane on 2009-05-23
when I run sudo ndiswrapper -m

I get:
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

module configuration contains directive install usb:v07D1p3B10d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 242.

module configuration contains directive install usb:v07D1p3B11d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete that at /usr/sbin/ndiswrapper-1.9 line 868, <MODPROBE> line 243.
module configuration already contains alias directive
```

I went to /usr/sbin/ndiswrapper-1.9 but I don't get it; I don't think line 868 should be deleted and 243 is a }.

4d

---

### Post by 67GTA on 2009-05-23
What is in /lib/modules/2.6.29*/kernel/ubuntu/ndiswrapper

---

### Post by 4dplane on 2009-05-23
It is what I tried to explain above but I said it kind of backwards. There is no file ndiswrapper nor a ubuntu folder in my /lib/modules/2.6.29*/kernel/ folder. Only in my older kernel folder is there such a file.

4d

---

### Post by 67GTA on 2009-05-23
Sounds like you have a vanilla kernel. Where did you get it? You will have to compile the kernel to add the modules.

---

### Post by 4dplane on 2009-05-23
AHH!! ok, a least I know what the problem is finaly... this is has been an all day adventure! I forget where I got it at the moment but I did it because there are some intel graphic problems with the older kernel. Of course you solve one problem and a new one shows up elsewhere. 

Can you point me in the right direction to what I am supposed to add to the kernel to get this working?

Thanks,
4d

---

### Post by 67GTA on 2009-05-24
I would suggest starting here first. There are easier solutions.

[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

To compile a custom kernel, you will have to download the kernel source from where ever you got it. It is also a very messy process. I would suggest booting into one of the other kernels you have installed, getting ndiswrapper set up, and get your internet working. Then try some of the solutions I linked to.

---

### Post by 4dplane on 2009-05-24
Thanks 67GTA, 

you made my day!!! \\:D/

4d

---


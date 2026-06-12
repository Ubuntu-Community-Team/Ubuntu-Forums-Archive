---
title: "newest nvidia drivers issue."
date: 2005-12-17
forum: Multimedia &amp; Video
---

### Post by drews_blunted on 2005-12-17
hey, i tryed manualy installing the latest nvidia drivers for ubuntu. They are not working out well and some games dont work now. Im trying to downgrade bad to the older version of the driver and use the nvidia-glx deb provided by ubuntu. how can i fully remove the newer nvidia driver 8*** i am getting a problem with my glx now!


Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by tseliot on 2005-12-17
[QUOTE=drews_blunted]hey, i tryed manualy installing the latest nvidia drivers for ubuntu. They are not working out well and some games dont work now. Im trying to downgrade bad to the older version of the driver and use the nvidia-glx deb provided by ubuntu. how can i fully remove the newer nvidia driver 8*** i am getting a problem with my glx now!


Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual[/QUOTE]

Set the driver back to "nv" in your xorg.conf.

Then try this command:

```
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run --uninstall
```

(of course you have to replace "NVIDIA-Linux-x86-1.0-XXXX-pkg1.run" with the name of the file you have got)

---

### Post by mo_x on 2005-12-17
If you had the Ubuntu deb installed before tried the latest nvidia driver then that is probably the cause of the problem. You need to remove all packages related to the nvidia driver with dpkg --purge before using the nvidia installer.

---

### Post by iluciv on 2005-12-19
I've also had a problem with installing the latest nvidia driver, though, it is the one from nvidia.com. 

I'm currently running the 7667 driver installed following tseliots guide (*see post above*.  When I restart after installing the new driver I get an API mismatch between the kernel module and the x module the kernel module being 7667 and the x module being 8174. 

**I have**
with out X running 
uninstalled the driver ```
sudo nvidia-installer --uninstall
```
installed the new driver ```
sudo sh N*8714*.run
```

Now this new driver can update the xorg.conf automatically ***nice one!! ***:) though seeing so it hasn't worked I've tried both methods with the install procedure

Ok then I get said error so I have further tried 
```
sudo rmmod nvidia
```
reinstall driver **no**

so I've decided to remove the kernel module 

```
sudo rm -f /lib/modules/2.6.12-10-k7/volatile/nvidia.ko
```
reinstall driver **no** :confused: 

after that I was at a loss so I just reinstalled the old 7667 driver 
**np** :???:

I must say, that the reason for the new installation, the old drivers seem to have broken (losing direct rendering) so I thought I'd install the new ones while I was at it.

---

### Post by mo_x on 2005-12-19
Here is a short howto for installing the latest nvidia driver I posted previously in another thread.
- Install compiler etc. and linux headers.
```
apt-get install build-essential
apt-get install linux-headers-`uname -r`
apt-get instal gcc-3.4
```
- Remove all packages related to nvidia driver with --purge option
```
sudo dpkg --purge nvidia-glx
sudo dpkg --purge nvidia-kernel-common
sudo dpkg --purge linux-restricted-modules-`uname -r`
```- Run the installer script (you may need a different version).
```
export CC=/usr/bin/gcc-3.4
sudo sh NVIDIA-Linux-x86_64-1.0-8174-pkg2.run
```

---

### Post by carina on 2006-01-09
Trying to do sudo dpkg --purge linux-restricted-modules-`uname -r`


```
carina@gingerelk:~$ sudo dpkg --purge linux-restricted-modules-`uname -r`
dpkg: dependency problems prevent removal of linux-restricted-modules-2.6.12-10-k7:
 linux-restricted-modules-k7 depends on linux-restricted-modules-2.6.12-10-k7.
dpkg: error processing linux-restricted-modules-2.6.12-10-k7 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-restricted-modules-2.6.12-10-k7
```

So I try to uninstall linux-restricted-modules-k7 first...

```
carina@gingerelk:~$ sudo dpkg --purge linux-restricted-modules-k7
dpkg: dependency problems prevent removal of linux-restricted-modules-k7:
 linux-k7 depends on linux-restricted-modules-k7.
dpkg: error processing linux-restricted-modules-k7 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-restricted-modules-k7
```

What now?

---

### Post by mo_x on 2006-01-09
Try to do this first:
sudo apt-get install linux-image-`uname -r`

---


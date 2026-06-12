---
title: "ATI Driver instilation Guide fails for me (From unoff. ati wiki)"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by Gruelius on 2007-10-30
Hey all,
I have a X1950pro card and i am looking to use a newer driver than the one supplied by ubuntu's repo's as it fixes video playback issues.

Anyway following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually) goes well untill the stage where it asks me to compile the kernel module. After running 

```
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx -f
sudo depmod -a
```

This is what i get 
```
julius@julius-desktop:~/Desktop$ sudo module-assistant prepare,update
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential
Reading package lists... 0%
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

the fglrx.ko file does not exist which is needed for the next stages. Im going to give ENVY a go at installing the ati fglrx driver but i have a feeling it wont work.

Anyway any help would be greatly appreciated :)

Julius

---


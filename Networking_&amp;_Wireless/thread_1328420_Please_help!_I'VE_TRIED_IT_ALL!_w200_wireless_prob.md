---
title: "Please help! I'VE TRIED IT ALL! w200 wireless problems."
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by dank_hippy on 2009-11-16
Hi. New User. New to Linux. Not an idiot... just for the record. :)

So, after much research, I've found that quite a lot of people have had problems getting the w200 multi-port wireless adapter to work for Ubuntu. I followed each and every step of the post:

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

And yet, until the very end. The module cannot be located. I seem to be having a problem with the modules or something.

I've also tried ndiswrapper. Followed every step of the installation instructions and still nothing. It cannot locate the module.

I think something may be happening here in the make install step that isn't going quite right that may have something to do with everything else.

root@ubuntu:~/ndiswrapper-1.55# make install
make -C driver install
make[1]: Entering directory `/home/luke/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/luke/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/luke/ndiswrapper-1.55/driver/crt.o
In file included from /home/luke/ndiswrapper-1.55/driver/crt.c:16:
/home/luke/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/luke/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
make[3]: *** [/home/luke/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/luke/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/luke/ndiswrapper-1.55/driver'
make: *** [install] Error 2
root@ubuntu:~/ndiswrapper-1.55# 

PLEASE. I don't want to keep Ubuntu hardwired... for the sake of my sanity I need to be able to move with my laptop.

People.Peace.Progress.Please and Thanks.Have a nice day.

---

### Post by gumshore on 2009-11-23
I am having the exact same probem, and now i cannot get ndiswrapper in the repositories or from source to work, and modprobe cannot find the module now!

---

### Post by seoirse on 2009-11-23
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?p=8373886#post8373886](http://ubuntuforums.org/showthread.php?p=8373886#post8373886)

and the solution I posted there. Hope that helps.

---

### Post by cariboo on 2009-11-23
Ndiswrapper is in the repositories, so ther is no need to compile it from source.

To use windows drivers make sure you have the windows drivers in your home directory. The driver I for my WUA-2340 consists of 5 files:

```
A5AGU.sys
ar5523.bin
DWLAB.dat
DWLInst.dll
NetA5AGU.cat
netA5AGU.inf
```

Your device may be different, if I remember correctly some only sonsist of 3 files. You do need at least the .inf and .sys files. to install the driver files, open a terminal and type:

```
sudo ndiswrapper -i /path_to/netA5AGU.inf
```

substitute your .inf file for the example above. Then to check if it found the device and the driver is setup type:

```
sudo ndiswrapper -l
```

that is a lower case L, this should show that the device has been found and what driver it is using. The output should look something like this:

[CODEsudo ndiswrapper -l
neta5agu : driver installed][/CODE]

Next type:

```
udo ndiswrapper -m
```

This writes a configuration file to /etc/modprobe.d, so that the driver is loaded on boot. The next thing to do is to load the module:

```
sudo modprobe ndiswrapper
```

If the module loads properly it will not display a message. to check if your device is enabled type:

```
dmesg | tail -n15
```

you should see an indication that your device is up.

---


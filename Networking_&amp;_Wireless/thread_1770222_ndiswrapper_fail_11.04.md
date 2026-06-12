---
title: "ndiswrapper fail 11.04"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by ezanqi on 2011-05-28
So I've just install ubuntu 11.04 and it's great and all that, but my brain is about to explode from trying to get my wireless adapter to work with ndiswrapper.

I seem to be able to get the driver installed:
```
$ ndiswrapper -l
oem11 : driver installed
	device (11AB:1FAA) present
```

but the ndiswrapper module is not being loaded:
```
$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

So I tried to build it from source, but that doesn't work even after applying the patch found in the stickied ndiswrapper troubleshooting thread:
```
$ sudo make
make -C driver
make[1]: Entering directory `/home/joey/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.38-8-generic M=/home/joey/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/joey/Desktop/ndiswrapper-1.56/driver/loader.o
/home/joey/Desktop/ndiswrapper-1.56/driver/loader.c:834:2: error: unknown field ‘ioctl’ specified in initializer
/home/joey/Desktop/ndiswrapper-1.56/driver/loader.c:834:2: warning: initialization from incompatible pointer type
make[3]: *** [/home/joey/Desktop/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/home/joey/Desktop/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/joey/Desktop/ndiswrapper-1.56/driver'
make: *** [all] Error 2

```

And that's where I'm stuck now. After doing a little more digging it's beginning to look like ndiswrapper isn't working with kernel 2.6.38, but hopefully I'm just missing something that one of you fine folks will be able to identify.

For the record, I'm using a Netgear WG311v3 PCI wireless adapter.

---

### Post by chili555 on 2011-05-29
When you see this:> make[3]: *** [/home/joey/Desktop/ndiswrapper-1.56/driver/loader.o] Error 1
make[2]: *** [_module_/home/joey/Desktop/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/joey/Desktop/ndiswrapper-1.56/driver'
make: *** [all] Error 2Then you are guaranteed to see this:```
FATAL: Module ndiswrapper not found.
```Why, pray tell, did you decide to build it from source? Did the Ubuntu built available on the install CD version not work for you? In what way?> I seem to be able to get the driver installed:Did you install the Windows 2K .inf file? Vista or 7 or ME or 3.0 won't work.

---

### Post by ezanqi on 2011-05-29
Sorry I wasn't clear, I was getting the module not found error before trying to build from source. I tried to build it because at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") there is a disclaimer that reads > "There is a known bug in these Debian packages, detailed in this thread. If you are having issues after installing from these packages, the kernel module may not have installed, so you may get the error FATAL: Module ndiswrapper not found when you run modprobe ndiswrapper in the terminal. To avoid this problem, it's best to compile from the source available at http://ndiswrapper.sourceforge.net/." which was exactly the error I was getting both fresh out of the box, and after trying to reinstall ndiswrapper using apt-get.
The driver I'm using is from Vista. I'm working on finding an XP or Win2k version now.

---

### Post by chili555 on 2011-05-29
Here is what I get:> chili@LAPTOP60:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.35-28-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       2.6.35-28-generic SMP mod_unload modversions 686 
chili@LAPTOP60:~$ sudo modprobe ndiswrapper
[sudo] password for chili: 
chili@LAPTOP60:~$ 
No error.

The thread that's quoted references kernel version 2.6.18; we are now up to 2.6.38. That's 215 years ago in Linux years.

I suggest you install the packages in the repos or on the CD and get the XP or 2K .inf file.

---

### Post by ezanqi on 2011-05-29
Well I started fresh and completely reinstalled 11.04 with a wired network connection, allowing Update Manager to do its thing. Installed Windows Wireless Drivers (ndisgtk) from the Software Center and downloaded the XP drivers for my wireless card. And it worked. I'm not sure why reinstalling the ndiswrapper packages didn't work on the first go round, but everything's working now.
Thanks for your help.

---

### Post by chili555 on 2011-05-29
Awesome! Glad it's working. Have fun.

---


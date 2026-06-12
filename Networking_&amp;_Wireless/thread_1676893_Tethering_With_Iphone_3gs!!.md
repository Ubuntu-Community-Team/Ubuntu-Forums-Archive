---
title: "Tethering With Iphone 3gs!!"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by freesparks on 2011-01-27
Hello all,

   Not sure if its appropriate to post this on this thread, so if it isn't I do apologize wholeheartedly.  Anyway, I am trying to use the my iphone's internet connection via usb tethering and in trying to do so, so far I've been able to mount the Iphone successfully and was even able to import photos, scary thought, and NO, my iphone is not jailbroken.  Moreover, all I want to do now is to use the tether feature using :

This is the website I obtained the info from:

> [http://superuser.com/questions/214117/how-to-use-iphone-internet-tethering-via-usb-with-ubuntu-10-04](http://superuser.com/questions/214117/how-to-use-iphone-internet-tethering-via-usb-with-ubuntu-10-04)

         And, the software packages are available in the synaptic package manager.
ipeth1.0,, and so far I got up to the point where the instructions on this websites makes mention to cd into this directory:

```

cd ~/ipheth/ipheth-driver$
```

and then to run:

```
make
```

I do that, and then I get this as a result:

```
make -C /lib/modules/2.6.35-25-generic/build M=/home/myname/ipheth/ipheth-driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/myname/ipheth/ipheth-driver/ipheth.o
/home/myname/ipheth/ipheth-driver/ipheth.c: In function ‘ipheth_alloc_urbs’:
/home/myname/ipheth/ipheth-driver/ipheth.c:137: error: implicit declaration of function ‘usb_buffer_alloc’
/home/myname/ipheth/ipheth-driver/ipheth.c:140: warning: assignment makes pointer from integer without a cast
/home/myname/ipheth/ipheth-driver/ipheth.c:147: warning: assignment makes pointer from integer without a cast
/home/myname/ipheth/ipheth-driver/ipheth.c:159: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/myname/ipheth/ipheth-driver/ipheth.o] Error 1
make[1]: *** [_module_/home/myname/ipheth/ipheth-driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [all] Error 2

```


Can't figure out why I am getting this error.  Has anyone stumbled on this?  Any help would be greatly appreciated.  Also, I do get:


> 
insmod: can't read 'ipheth.ko': No such file or directory

, when I run:

> :~/ipheth/ipheth-driver$ sudo insmod ipheth.ko

this in the Terminal.  And when I run:

```
dmesg | grep iPhone
```

I get this:

```
[  294.413285] ipheth 2-4:4.2: Apple iPhone USB Ethernet device attached
```




Best Regards,

freesparks

---


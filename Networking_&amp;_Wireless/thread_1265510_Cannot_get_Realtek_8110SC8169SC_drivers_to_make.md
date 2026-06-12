---
title: "Cannot get Realtek 8110SC/8169SC drivers to make"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by TennSeven on 2009-09-13
I am running Ubuntu 9.04 (Jaunty Jackalope), kernel 2.6.28-15-generic. I have a motherboard with built-in wireless:

```
jrock@jrocklinux:/tmp/r8169-6.011.00$ lspci | grep Ethernet
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

The problem I am trying to solve is that my wireless signal is very weak in Ubuntu (I VERY occasionally boot to a Vista partition on the same machine and the signal strength is fine).  As a result, I am getting slow data transfer rates and my wireless is occasionally dropping.

I have downloaded Realtek's linux and as per Realtek's readme file, have unpacked it into a directory at "/tmp/r8169-6.011.00," have run "rmmod r8169" and have run "sudo make clean."  When I try to run "sudo make modules" I get the following output:

```
jrock@jrocklinux:/tmp/r8169-6.011.00$ sudo make modules
make -C src/ modules
make[1]: Entering directory `/tmp/r8169-6.011.00/src'
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/tmp/r8169-6.011.00/src'
make: *** [modules] Error 2
jrock@jrocklinux:/tmp/r8169-6.011.00$ 
```

Of course, since this didn't work, I get an error when I run "make install" as well:

```
jrock@jrocklinux:/tmp/r8169-6.011.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/tmp/r8169-6.011.00/src'
install -m 744 -c r8169.ko /lib/modules/2.6.28-15-generic/kernel/drivers/net/
install: cannot stat `r8169.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/tmp/r8169-6.011.00/src'
make: *** [install] Error 2
jrock@jrocklinux:/tmp/r8169-6.011.00$
``` 

I have done some forum searching and apparently others have had this problem but I could not find a solution that seemed to make sense.  I did install and unpack the linux kernel code after reading one of the other posts, but it did not help.  Can anyone help me figure out how to fix this error so I can install the driver?

Thank you in advance,

TennSeven

---

### Post by TennSeven on 2009-09-17
No one? Does anyone at least have a recommendation as to what wireless network card I should get so I don't have to deal with the network manager thinking I am only getting 14% signal strength?

Better yet, does anyone know of any other way to fix this issue with the card I already have?

Thanks.

---

### Post by Crafty Kisses on 2009-09-17
Not sure if you have the **build-essential** package installed, but try installing that package then get back to me, if you're still having issues I will continue to help you. You can run in the terminal:
```
sudo apt-get install build-essential
```

---


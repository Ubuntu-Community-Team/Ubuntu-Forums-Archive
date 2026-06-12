---
title: "compiling amedyn usb adsl modem driver: /lib/modules/2.6.10-6-386/build not found"
date: 2006-03-15
forum: Networking &amp; Wireless
---

### Post by bernardfrancois on 2006-03-15
Hi,

I'm trying to compile the [amedyn driver](http://sourceforge.net/projects/aam6000ug) for a compatible asus adsl modem (*asus aam6000ug*).

When I run 'make' I get the following output: 

```

cd init && make clean
make[1]: Entering directory `/usr/amedyn/init'
rm -f amload amioctl amloaddbg amloaddbgt 
make[1]: Leaving directory `/usr/amedyn/init'
cd module && make clean
make[1]: Entering directory `/usr/amedyn/module'
rm -f *.o .*.flags *.ko *.mod.* .*.o.cmd .*.ko.cmd
make[1]: Leaving directory `/usr/amedyn/module'
cd bridged && make clean
make[1]: Entering directory `/usr/amedyn/bridged'
rm -f br2684ctl 
make[1]: Leaving directory `/usr/amedyn/bridged'
cd amcontrol && make clean
make[1]: Entering directory `/usr/amedyn/amcontrol'
rm -f amcontrol amcontroldbg amcontroldbgt 
make[1]: Leaving directory `/usr/amedyn/amcontrol'
cd init && make && make install
make[1]: Entering directory `/usr/amedyn/init'
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amload.c -o amload
gcc -O2 -Wstrict-prototypes -fomit-frame-pointer -pipe -march=i686 -Wall -DLINUX -Wsign-compare -I../include -lusb  amioctl.c -o amioctl
make[1]: Leaving directory `/usr/amedyn/init'
make[1]: Entering directory `/usr/amedyn/init'
install -c -m 755 -p amload amioctl /usr/sbin
make[1]: Leaving directory `/usr/amedyn/init'
cd firmware && make
make[1]: Entering directory `/usr/amedyn/firmware'
install -c -m 644 -p fw-usb.bin Fw-usb_A.bin /usr/sbin
make[1]: Leaving directory `/usr/amedyn/firmware'
cd module && make && make install
make[1]: Entering directory `/usr/amedyn/module'
rm -f xdslusb_2.6.o
make -C /lib/modules/2.6.10-6-386/build SUBDIRS=/usr/amedyn/module XDSLUSB-MODULE=amedyn modules
make: *** /lib/modules/2.6.10-6-386/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [normal] Error 2
make[1]: Leaving directory `/usr/amedyn/module'
make: *** [AME_MODULE] Error 2

```

As you can see, the error is indicated by the following line:
**make: *** /lib/modules/2.6.10-6-386/build: No such file or directory.  Stop.**

I can confirm there is no such directory. However, I have the /lib/modules/2.6.10-6-386 directory and some underlying directories.
Note that I do have the **linux-kernel-headers** package and that **uname -r** shows me that I indeed have kernel version *2.6.10-6-386*.

I have the following packages:
```

linux-kernel-headers
libusb-0.1-4
libusb-dev
libatm1
libpcap0.8
libpcap0.7

```

This is the list of packages I should have, mentioned in the documentation.
```

kernel-source
ppp
libpcap0 (also called libpcap ;) )
ppp-pppoatm (IF you are using pppoatm)
rp-pppoe (IF you are using pppoe)
libusb
libusb-dev
linux-atm 

```
I didn't install rp-ppoe since it's not needed to compile the driver and I would like to use pppoeconf (rp-ppoe isn't in the repositories neither).

I think the Makefile that came with amedyn isn't aware of the location of some directory and is looking in a directory named *build*, which doesn't exits on Ubuntu. Creating a link would be a solution, but I don't know where it should point to...

Can someone help me out please? Thanks in advance!

---

### Post by bernardfrancois on 2006-03-15
I found that I had to install **linux-source-2.6.10** in synaptic. I did, and then I executed the following commands to create a symlink:

```

cd /usr/src
bunzip2 linux-source-2.6.10.tar.bz2
tar -xzvhf linux-source-2.6.10.tar 
ln -s /usr/src/linux-source-2.6.10 /lib/modules/2.6.10-6-386/build

```

When I run 'make' this time, I still get errors:
```

make -C /lib/modules/2.6.10-6-386/build SUBDIRS=/usr/amedyn/module XDSLUSB-MODULE=amedyn modules
make[2]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
/usr/amedyn/module/Makefile:35: *** USB support not turned on in the kernel!.  Stop.
make[2]: *** [_module_/usr/amedyn/module] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.10'
make[1]: *** [normal] Error 2
make[1]: Leaving directory `/usr/amedyn/module'
make: *** [AME_MODULE] Error 2

```

---


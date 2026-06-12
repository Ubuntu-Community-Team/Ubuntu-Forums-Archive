---
title: "Ceton Linux driver no longer loads in Kernel 3.16.0-45"
date: 2015-08-21
forum: Mythbuntu
---

### Post by Chadarius on 2015-08-21
I had to roll back to 3.16.0-33 on my Ubuntu Mythtv server for the driver to load. I get the following error when the driver tries to load in 3.16.0-45:
modprobe: ERROR: could not insert 'ctn91xx': Exec format error

When I run dmesg I get the following error:
ctn91xx: disagrees about version of symbol module_layout

I then tried to manually compile and install the driver again and it compiles fine. Yes, I have all the kernel headers and sources installed. It just won't load properly afterwards.

I created a DKMS setup for the driver which works great by the way (as long as its not the latest kernel that is!). You can check it out at [http://chadarius.com/content/setup-dkms-ceton-infinitv-drivers-ubuntu](http://chadarius.com/content/setup-dkms-ceton-infinitv-drivers-ubuntu). This makes it easy to upgrade Ubuntu without having to manually recompile your driver each time. It worked great for a number of kernel updates until this last one. :)

Anyone else having this issue with newer kernels? Or am I messing something up?

---

### Post by Karl_Shea on 2015-08-30
I actually used your exact writeup to set up DKMS on my Ubuntu 14.04 machine, and I'm running 3.16.0-45-generic with no issue.

Maybe try reverting to an older kernel and uninstalling/reinstalling the newer one?

```
root@citywall:/usr/src/ctn91xx-2013_0326_2226# cat dkms.conf
MAKE="make"
CLEAN="make clean"
BUILT_MODULE_NAME=ctn91xx
DEST_MODULE_LOCATION=/extra/
BUILT_MODULE_LOCATION=
PACKAGE_NAME=ctn91xx
PACKAGE_VERSION=2013_0326_2226
AUTOINSTALL=yes
REMAKE_INITRD=yes
```

```
root@citywall:~# dmesg | grep -i ctn
[    1.242234] ctn91xx: module verification failed: signature and/or  required key missing - tainting kernel
[    1.242434] ctn91xx_print_compilation:17 : (-1) driver compiled at 00:13:09 on Jul 28 2015
[    1.243285] ctn91xx 0000:01:00.0: enabling device (0000 -> 0002)
[    1.243362] ctn91xx_register:69 : (0) IO hw_reg_base address: f7c00000
[    1.243363] ctn91xx_register:70 : (0) reg_base: ffffc90004b80000
[    1.243370] ctn91xx_register:78 : (0) IO translation_hw_reg_base address: f7c20000
[    1.243372] ctn91xx_register:79 : (0) translation_reg_base: ffffc90004be0000
[    1.243380] ctn91xx_register:117 : (0) system clock freq 100000000, ticks per us 100
[    1.243384] ctn91xx_reset_all:103 : (0) reset all
[    1.245344] ctn91xx_register:181 : (0) Driver initialization successful for CTN-9120 v6252 board 0
[    1.245770] ctn91xx_register:205 : (0) irq: 16
[    1.245776] ctn91xx_delayed_slot_number_worker:321 : (0) sending slot number 0
[    1.269462] ctn91xx_interrupt_rpc_ack_recvd:100 : (0) dropping interrupt type 55, no listeners
```

---

### Post by Karl_Shea on 2015-09-05
I had the same problem with 3.16.0-48-generic. I did this and rebooted and it worked:

```
dkms remove -m ctn91xx -v 2013_0326_2226 --all
dkms add -m ctn91xx -v 2013_0326_2226
dkms build -m ctn91xx -v 2013_0326_2226
dkms install -m ctn91xx -v 2013_0326_2226
```

---

### Post by Chadarius on 2015-09-08
I am going to try this right now. I'll let you know if it fixes the problem.

---

### Post by Chadarius on 2015-09-08
Bless you Karl! That totally worked! :)

Now let's hope that the DKMS setup continues to work going forward.

---

### Post by Scott_Johnson on 2015-09-08
What kinds of issues were you seeing with the Ceton card in 14.04?  I recently installed an Infinitv 4 with 14.04 and was able to install the drivers to the card but I'm having issues getting the tuners to work.  All 4 are Red and my Tuning Adapter TR Status is Disabled.  I can't seem to get beyond that point..

---

### Post by Karl_Shea on 2015-09-09
Other than the recent issue with the driver for this latest kernel, which seems to be easy to resolve, I haven't had any issues with the card at all. Although I have the 6-tuner card, so I'm not sure if that makes a difference.

Is it possible you have a problem with your CableCARD?

---

### Post by Chadarius on 2015-09-09
I haven't had any issues at all besides this compiling one. Its been working great. I assume your cable company was able to program the card successfully? Do you have the latest firmware from [http://www.thegreenbutton.tv/forums/viewtopic.php?f=68&t=8352](http://www.thegreenbutton.tv/forums/viewtopic.php?f=68&t=8352).

---

### Post by Karl_Shea on 2015-09-13
> **Chadarius said:**
> Bless you Karl! That totally worked! :)

Now let's hope that the DKMS setup continues to work going forward.

I think I figured out what was going on. If you look in the Makefile, it's finding the kernel version to build against using $(shell uname -r) and assigning it to KERNEL_VERSION, which it then uses to build the KERNEL_DIR path to find the headers.

The problem is that when DKMS builds the module, it's still running on the old kernel so it's getting built against the wrong headers. DKMS passes in the *new* kernel using the KERNELRELEASE environment variable, but that's not what the Ceton Makefile uses.

If you change the dkms.conf MAKE line to read:

```
MAKE="make KERNEL_VERSION=${kernelver}"
```

it should start building against the version that's getting installed instead.

---

### Post by Chadarius on 2015-09-14
Brilliant! :)

---


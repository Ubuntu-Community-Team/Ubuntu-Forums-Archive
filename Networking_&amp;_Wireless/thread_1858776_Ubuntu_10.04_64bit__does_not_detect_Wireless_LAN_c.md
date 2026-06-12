---
title: "Ubuntu 10.04 64bit : does not detect Wireless LAN carriers"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by mamboknave on 2011-10-13
System (laptop): HP Pavilion g6-1c77nr
Operating system: Ubuntu 10.04 64bit, kernel 2.6.32-33

Problem: this system cannot detect the Wireless LAN carrier.

Assumption: the system does not have the correct Wireless LAN driver.

Looking at the HP support site and talking to the folks there, it seems that this laptop is integrating the Realtek RTL8188CE as Wireless LAN adapter.

Therefore, from Realtek.com I did download the Linux driver for kernel 2.6.34 (and earlier).

I followed the instructions in the readme.txt (embedded in the driver tar file) and tried to install the driver.

It failed at this point (see the Error 2):

user@user-LT:~/Downloads/rtl8192ce_linux_2.6.0006.0321.2011$  sudo make install

make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make[1]: Entering directory `/home/paolo/Downloads/rtl8192ce_linux_2.6.0006.0321.2011/HAL/rtl8192'
make -C /lib/modules/2.6.32-33-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/paolo/Downloads/rtl8192ce_linux_2.6.0006.0321.2011/HAL/rtl8192'
make: *** [install] Error 2


Consequently, the command 'iwconfig' responds that there is 'no wireless extensions'

Can you please help me to resolve this problem? It's *seriously* impacting my work.

---

### Post by mamboknave on 2011-10-13
Ok, thanks to the insights of anothermikemiller in the [**post# 1526849**]("http://ubuntuforums.org/showthread.php?t=1526849") I made it kind* of working.

Although 'make install' failed, it created locally a good driver: r8192ce_pci.ko

I renamed that driver as r8192_pci.ko and placed in:
/lib/modules/2.6.32-33-generic/kernel/drivers/staging/rtl8192e/

Then I added the line r8192_pci in the file /etc/modules and run the command sudo insmod r8192_pci.ko

The system now connects to the wireless LAN carrier.

(*) I say 'kind of working' because this is a very brute-force workaround that may issue other consequences.

Hence, I would greatly appreciate a cleaner solution if someone knows.

Looking fwd...

---

### Post by Dr. C on 2011-10-16
I have a HP ProBook 4530s with the RTL8188CE chipset and the wireless works out of the box at 150n with Ubuntu 11.10 64bit. I must say that over the years I have found this a lot with wireless on Ubuntu. Problematic first and then works out of the box one or two releases later.

---


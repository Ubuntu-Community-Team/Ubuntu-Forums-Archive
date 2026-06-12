---
title: "Trying to Install driver for RTL8101E/RTL8102E - ISSUE"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by manuleka on 2009-01-29
i'm trying to install driver for my RTL8101E/RT8102E for my laptop... i had issues with it after a kernel update... here are commands for building from source
i got stuck on first one - i'm a newbie but just trying out following instructions provided on driver download
---- instructions ----
# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# insmod ./src/r8101.ko	(or r8101.o for kernel 2.4.x)
----

```

manu@wind:~/Dwnlds/aps/RTL8101E-RTL8102E-Ubuntu-Driver/r8101-1.011.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/manu/Dwnlds/aps/RTL8101E-RTL8102E-Ubuntu-Driver/r8101-1.011.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/home/manu/Dwnlds/aps/RTL8101E-RTL8102E-Ubuntu-Driver/r8101-1.011.00/src'
make -C src/ modules
make[1]: Entering directory `/home/manu/Dwnlds/aps/RTL8101E-RTL8102E-Ubuntu-Driver/r8101-1.011.00/src'
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/manu/Dwnlds/aps/RTL8101E-RTL8102E-Ubuntu-Driver/r8101-1.011.00/src'
make: *** [modules] Error 2
manu@wind:~/Dwnlds/aps/RTL8101E-RTL8102E-Ubuntu-Driver/r8101-1.011.00$ 

```

---

### Post by jjhuopa on 2009-02-07
I have the same problem. I downloaded the linux driver r8101-1.011.00.tar.bz2 from the Realtek site, got the same errors as you..

---

### Post by manuleka on 2009-02-07
try this:

unpack your download... 

in terminal go to the unpacked folder then run these commands

[NOTE: i'm using RTL8101E and Ubuntu 8.10]

```

sudo -E make clean modules  
sudo make install  
sudo depmod -a
blacklist r8169
sudo update-initramfs -u 

```

hope your problem will be fixed

---

### Post by james.walmsley on 2009-02-10
This didn't fix my problem. Same hardware but ethernet still not working in Ubuntu.

Realtek a really rubbish.

---

### Post by manuleka on 2009-02-12
thats not good... mine worked after running the above commands... 

just try these 3 first, then reboot and see if it works

```

sudo -E make clean modules  
sudo make install  
sudo depmod -a

```

---

### Post by jjhuopa on 2009-02-23
Hi! Tried this again after a small break from Ubuntu: I tried Debian GNU/Linux "Lenny" and with that the ethernet worked, but otherwise I found Debian a bit complicated. But the Realtek chip must work in Linux since it worked with Lenny. But now I decided to put Xubuntu 8.10 on my minilaptop and tried the commands below, but still the ethernet doesn't work.

sudo -E make clean modules  
sudo make install  
sudo depmod -a

I didn't try:

blacklist r8169
sudo update-initramfs -u

Because blacklist wasn't recognized as a command. Are these two commands needed? Any idea why Xubuntu didn't recognize blacklist?

Thanks!

---

### Post by jjhuopa on 2009-02-24
Ok so I figured out the blacklist thing with my friend Google. I added **blacklist r8169** to /etc/modbprobe.d/blacklist and did **sudo update-initramfs -u** and rebooted. For my surprise I couldn't boot into the newest kernel 2.6.27-11-generic any more. My laptop wen't into a catatonic state and didn't react to any button so I had to pull the battery off. But the I could boot into the kernel 2.6.27-7-generic and in that the ethernet worked! I thought I could just remove the newest kernel but then again the ethernet didn't work, so installed it again. Just commented out the newest kernel in /boot/grub/menu.lst and everything is fine!

Thanks!:guitar:

---


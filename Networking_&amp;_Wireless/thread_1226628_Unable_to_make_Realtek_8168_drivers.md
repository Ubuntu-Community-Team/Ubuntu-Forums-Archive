---
title: "Unable to make Realtek 8168 drivers"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by palmboy5 on 2009-07-29
Following this thread:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=671614](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=671614)

I am trying to replace the 8169 driver with the official Realtek driver for 8168. I have followed Realtek's readme as far as deleting the 8169 driver, but I cannot compile the new driver.

I get this:
```
vcn64ultra@Diamondville:~/Junk/Realtek Ethernet/r8168-8.012.00$ ls
Makefile  readme  src
vcn64ultra@Diamondville:~/Junk/Realtek Ethernet/r8168-8.012.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
make -C src/ modules
make[1]: Entering directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
make -C /lib/modules/2.6.28-13-server/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-server'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-server'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
make: *** [modules] Error 2
vcn64ultra@Diamondville:~/Junk/Realtek Ethernet/r8168-8.012.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.28-13-server/kernel/drivers/net/
install: cannot stat `r8168.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
make: *** [install] Error 2
vcn64ultra@Diamondville:~/Junk/Realtek Ethernet/r8168-8.012.00$ sudo depmod -a
vcn64ultra@Diamondville:~/Junk/Realtek Ethernet/r8168-8.012.00$ sudo modprobe r8168
FATAL: Module r8168 not found.
```

I am using Ubuntu 9.04 Server with ubuntu-desktop installed. How do I get it to compile the driver? :confused:

---

### Post by martinbaselier on 2009-07-29
I see a lot of commands, but i'm missing make (without any options) to build the driver.

---

### Post by palmboy5 on 2009-07-29
> **martinbaselier said:**
> I see a lot of commands, but i'm missing make (without any options) to build the driver.

I was following the readme instructions:
```
<Quick install with proper kernel settings>
	Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
		# lsmod | grep r8169

	If it is installed, please remove it.
		# rmmod r8169
	note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

	Unpack the tarball :
		# tar vjxf r8168-8.aaa.bb.tar.bz2

	Change to the directory:
		# cd r8168-8.aaa.bb

	If you are running the target kernel, then you should be able to do :

		# make clean modules	(as root or with sudo)
		# make install
		# depmod -a
		# modprobe r8168
```

---

### Post by palmboy5 on 2009-07-30
Am I missing some sort of dependency or what?:confused:

---

### Post by martinbaselier on 2009-07-30
make clean normally is used to clean the directory after an unsuccessful run of make or after making some changes to the source. I think in this case the command is combined, make clean, then it runs make modules

The problem seems to be here:
> 
make -C src/ modules
make[1]: Entering directory `/home/vcn64ultra/Junk/Realtek Ethernet/r8168-8.012.00/src'
make -C /lib/modules/2.6.28-13-server/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-server'
scripts/Makefile.build:41: /src/Makefile: No such file or directory

the problem seems to be that it's looking for /src/Makefile
I don't know what it expects to be there. You could make a symbolic link: (just copy this and paste it into a terminal
**sudo ln -s /usr/src/linux-headers-`uname -r` /src**
Maybe you need the kernel source though. 
sudo apt-get install linux-source
After installing you would need to unpack it:
**cd /usr/src**
**sudo tar -xjf linux-source-2.6.28.tar.bz2 **
then delete the symbolic link:
**rm /src**
and create a new one:
**ln -s /usr/src/linux-source-2.6.28/ /src**

---

### Post by palmboy5 on 2009-07-30
For your instructions, I hit a dead end at rm /src where it says it cannot delete because its a directory. The new source has downloaded and extracted successfully, at least.

I then went on cluelessly into /src/ and accidentally deleted virtually everything in it.. but now the readme instructions have this change:
```
vcn64ultra@Diamondville:~/Junk/RealtekEthernet/r8168-8.012.00$ sudo make modules
make -C src/ modules
make[1]: Entering directory `/home/vcn64ultra/Junk/RealtekEthernet/r8168-8.012.00/src'
make -C /lib/modules/2.6.28-13-server/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-server'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-server'
strip --strip-debug r8168.ko
strip: 'r8168.ko': No such file
make[1]: *** [modules] Error 1
make[1]: Leaving directory `/home/vcn64ultra/Junk/RealtekEthernet/r8168-8.012.00/src'
make: *** [modules] Error 2
vcn64ultra@Diamondville:~/Junk/RealtekEthernet/r8168-8.012.00$ sudo make install
make -C src/ install
make[1]: Entering directory `/home/vcn64ultra/Junk/RealtekEthernet/r8168-8.012.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.28-13-server/kernel/drivers/net/
install: cannot stat `r8168.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/vcn64ultra/Junk/RealtekEthernet/r8168-8.012.00/src'
make: *** [install] Error 2
vcn64ultra@Diamondville:~/Junk/RealtekEthernet/r8168-8.012.00$ 
```

Looks like something got built.. I guess thats an improvement?

---

### Post by palmboy5 on 2009-08-01
Anyone have any success building the RTL8168 drivers in Ubuntu 9.04?

---

### Post by Idefix82 on 2009-08-01
The easiest way is to just execute this script:
[http://www.jamesonwilliams.com/hardy-r8168]("http://www.jamesonwilliams.com/hardy-r8168")

Just download the linked tar into your home directory, then run the first three lines of the howto.

What ethernet card do you have?

---

### Post by palmboy5 on 2009-08-02
The script successfully compiled the driver and stuff and till now I've been testing to see if my network issues went away. They do seem to be gone, thanks for your help!

I made one change to the script before running though, which was changing the version number to the most recent and copying the most recent tarball into the directory for it to use instead of its own (which was, of course, older).

---


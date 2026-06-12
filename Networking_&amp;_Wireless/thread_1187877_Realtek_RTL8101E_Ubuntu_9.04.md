---
title: "Realtek RTL8101E Ubuntu 9.04"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by Lawliet7 on 2009-06-15
Hello i got a Realtek RTL8101E wireless card , and i install Ubuntu 9.04 , everything looks fine , i see wireless networks and i can connect to them but i dont have internet i know i must install other driver i found something like this instruction :

1. Download and install lasted drivers from([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)) follow instruction include that package.

2. Deactive old driver:

    mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko.old
    depmod -a

3. Generate new initrd.img

    mv /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.old
    mkinitramfs -o /boot/initrd.img-`uname -r`

**But instruction How to install driver looks like this :** 
<Quick install with proper kernel settings>
    Check whether the built-in driver, r8169.ko (or r8169.o for kernel 2.4.x), is installed. 
        # lsmod | grep r8169

    If it is installed, please remove it.
        # rmmod r8169
    note: If the built-in driver cannot removed by rmmod, please edit /etc/modprobe.conf and comment 'alias eth0 r8169'. Then, remmove it again or reboot your computer.

    Unpack the tarball :
        # tar vjxf r8101-1.aaa.bb.tar.bz2

    Change to the directory:
        # cd r8101-1.aaa.bb

    If you are running the target kernel, then you should be able to do :

        # make clean modules    (as root or with sudo)
        # make install
        # depmod -a
        # modprobe r8101

    You can check whether the driver is loaded by using following commands.

        # lsmod | grep r8101
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. Then, you can use the following command to activate 
    the ethX.

This is what i do , i have done only remove old driver and r8169 does not exist :

**user@P:~$ rmmod r8169 **
ERROR: Module r8169 does not exist in /proc/modules 
**user@P:~$ sudo tar vjxf /home/user/Pulpit/r8101-1.012.00.tar.bz2 **
[sudo] password for user: 
r8101-1.012.00/ 
r8101-1.012.00/src/ 
r8101-1.012.00/src/rtl_ethtool.h 
r8101-1.012.00/src/rtl_eeprom.h 
r8101-1.012.00/src/r8101_n.c 
r8101-1.012.00/src/Makefile 
r8101-1.012.00/src/rtl_eeprom.c 
r8101-1.012.00/src/Makefile_linux24x 
r8101-1.012.00/src/r8101.h 
r8101-1.012.00/Makefile 
r8101-1.012.00/readme 
**user@P:~$ cd r8101-1.012.00** 
**user@P:~/r8101-1.012.00$ sudo make clean modules **
make -C src/ clean 
make[1]: Entering directory `/home/user/r8101-1.012.00/src' 
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order 
make[1]: Leaving directory `/home/user/r8101-1.012.00/src' 
make -C src/ modules 
make[1]: Entering directory `/home/user/r8101-1.012.00/src' 
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/src modules 
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic' 
scripts/Makefile.build:41: /src/Makefile: No such file or directory 
make[3]: *** No rule to make target `/src/Makefile'.  Stop. 
make[2]: *** [_module_/src] Error 2 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make[1]: *** [modules] Error 2 
make[1]: Leaving directory `/home/user/r8101-1.012.00/src' 
make: *** [modules] Error 2 
**user@P:~/r8101-1.012.00$ sudo make install **
make -C src/ install 
make[1]: Entering directory `/home/user/r8101-1.012.00/src' 
install -m 744 -c r8101.ko /lib/modules/2.6.28-11-generic/kernel/drivers/net/ 
install: cannot stat `r8101.ko': No such file or directory 
make[1]: *** [install] Error 1 
make[1]: Leaving directory `/home/user/r8101-1.012.00/src' 
make: *** [install] Error 2

What I'm doing wrong  ?:(

---

### Post by Lawliet7 on 2009-06-15
please any one?

---

### Post by Iowan on 2009-06-15
For what it's worth - my laptop uses the Realtek RTL8101E wireless card. It is using the r8169 driver and seems to connect to wifi hotspots without problem - I haven't tried setting up wifi here at home, yet.

---

### Post by RameshRao on 2009-08-24
> **Lawliet7 said:**
> please any one?

Hope you have figured it by now. For those that have stumbled into this thread later, here is a fix. I followed instructions from [http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/#more-8](http://en.alessiotreglia.com/articles/realteks-modules-new-version-has-been-released/#more-8) 

and

'sudo -E make clean modules' seems to work.

Regards,
Ramesh

---


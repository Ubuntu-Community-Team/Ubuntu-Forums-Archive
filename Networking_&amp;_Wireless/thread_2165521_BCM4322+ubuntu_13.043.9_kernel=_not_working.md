---
title: "BCM4322+ubuntu 13.04/3.9 kernel= not working"
date: 2013-08-05
forum: Networking &amp; Wireless
---

### Post by npm1 on 2013-08-05
Hello,
I've got ubuntu 13.04 installed.
My BCM4322 is not working in 13.04 that has a kernel 
3.9.2-030902-generic
can someone help me please
the STA in additional drivers doesn't work...
Heres one of the guidz i followed:
[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)
i 've also tried other guidz but they all including the above seem like they are based of off older versions of ubuntu...please help

thanks

---

### Post by chili555 on 2013-08-05
Let's see exactly which Broadcom you have. Please open a terminal and run and post:```
lspci -nn -d 14e4:
```Thanks.

---

### Post by npm1 on 2013-08-05
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

---

### Post by chili555 on 2013-08-05
The STA driver is correct for your device. Did it not install correctly or did it install and won't connect or...??> the STA in additional drivers doesn't work...^^^What does this mean?

What is the result of:```
sudo apt-get install --reinstall bcmwl-kernel-source
```This package required linux-headers-generic. When you installed the 3.9 kernel, did you also install linux-headers?

---

### Post by npm1 on 2013-08-07
```
SATELLITE-PRO-C850-10W:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for :
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtiff4 libtiffxx0c2 linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 241 not upgraded.
Need to get 0 B/1,346 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 313578 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.9.2-030902-generic
Building for architecture x86_64
Building initial module for 3.9.2-030902-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.9.2-030902-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.9.2-030902-generic
```

---

### Post by npm1 on 2013-08-07
Upgrading the kernel gives the following:
I have found this thread interms of the missing file:
[http://ubuntuforums.org/showthread.php?t=1892321&page=2](http://ubuntuforums.org/showthread.php?t=1892321&page=2)
BUT MY KERNEL is beyond this year...

Heres what i get when upgrading the kernel in ubuntu 13.04

```
SATELLITE-PRO-C850-10W:~$ cd Downloads
SATELLITE-PRO-C850-10W:~/Downloads$ cd K310
SATELLITE-PRO-C850-10W:~/Downloads/K310$ sudo dpkg -i linux*.deb
Selecting previously unselected package linux-headers-3.10.5-031005.
(Reading database ... 313578 files and directories currently installed.)
Unpacking linux-headers-3.10.5-031005 (from linux-headers-3.10.5-031005_3.10.5-031005.201308040618_all.deb) ...
Selecting previously unselected package linux-headers-3.10.5-031005-generic.
Unpacking linux-headers-3.10.5-031005-generic (from linux-headers-3.10.5-031005-generic_3.10.5-031005.201308040618_amd64.deb) ...
Selecting previously unselected package linux-image-3.10.5-031005-generic.
Unpacking linux-image-3.10.5-031005-generic (from linux-image-3.10.5-031005-generic_3.10.5-031005.201308040618_amd64.deb) ...
Done.
Setting up linux-headers-3.10.5-031005 (3.10.5-031005.201308040618) ...
Setting up linux-headers-3.10.5-031005-generic (3.10.5-031005.201308040618) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
Traceback (most recent call last):
File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.10.5-031005-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
Setting up linux-image-3.10.5-031005-generic (3.10.5-031005.201308040618) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
Traceback (most recent call last):
File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.10.5-031005-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
update-initramfs: Generating /boot/initrd.img-3.10.5-031005-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.9.2-030902-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Writing config for /boot/vmlinuz-3.8.0-18-generic...
P: Writing config for /boot/vmlinuz-3.4.27-030427-generic...
P: Writing config for /boot/vmlinuz-3.10.5-031005-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.10.5-031005-generic /boot/vmlinuz-3.10.5-031005-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.10.5-031005-generic
Found initrd image: /boot/initrd.img-3.10.5-031005-generic
Found linux image: /boot/vmlinuz-3.9.2-030902-generic
Found initrd image: /boot/initrd.img-3.9.2-030902-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-18-generic
Found initrd image: /boot/initrd.img-3.8.0-18-generic
Found linux image: /boot/vmlinuz-3.4.27-030427-generic
Found initrd image: /boot/initrd.img-3.4.27-030427-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```

---

### Post by QIII on 2013-08-07
npm1 --

Please use standard fonts and colors as well as code tags around code.


Thanks.

---

### Post by chili555 on 2013-08-07
> Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.So what does it report?```
cat /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log | tail -n20
```Where did you get your kernel? Did you also install linux-image-*extra* and linux-headers??

The missing firmware for your ethernet card is a whole different issue unrelated to wireless. Unless your ethernet isn't performing well, let's save that until the wireless is working.

---

### Post by npm1 on 2013-08-07
this is what it says:
```
DKMS make.log for bcmwl-6.20.155.1+bdcom for kernel 3.10.5-031005-generic (x86_64)
Wed Aug  7 20:56:33 BST 2013
make: Entering directory `/usr/src/linux-headers-3.10.5-031005-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2704:7: warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2704:7: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2707:4: warning: passing argument 1 of ‘wl->tkipmodops->print_stats’ from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2707:4: note: expected ‘struct seq_file *’ but argument is of type ‘char *’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c: In function ‘wl_reg_proc_entry’:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2917:2: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2917:22: warning: assignment makes pointer from integer without a cast [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2922:16: error: dereferencing pointer to incomplete type
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2923:16: error: dereferencing pointer to incomplete type
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.c:2924:16: error: dereferencing pointer to incomplete type
cc1: some warnings being treated as errors
make[1]: *** [/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.10.5-031005-generic'
```

---

### Post by npm1 on 2013-08-07
I got the kernel from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
quidsup's instructions

---

### Post by chili555 on 2013-08-07
I suspect the issue is that the bcmwl-kernel-source package is built for kernel version 3.8 and you are trying to install it on 3.10. Is the result the same if you boot into 3.9 at the GRUB menu? You might try the 13.10 (Saucy) version from here: [http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source](http://packages.ubuntu.com/search?keywords=bcmwl-kernel-source)

---

### Post by npm1 on 2013-08-08
Hi,
The picture you have as you're avater, matchs you perferctly.
Thanks for your time and patience.
As that has solved my issue.

So for the future i would have to look for the driver that matchs my kernel...simple as....

Thanks....

---

### Post by chili555 on 2013-08-08
> **npm1 said:**
> 
So for the future i would have to look for the driver that matchs my kernel...simple as....

Pretty much! I'm glad it's working. Call the doctor again if you need me!

---


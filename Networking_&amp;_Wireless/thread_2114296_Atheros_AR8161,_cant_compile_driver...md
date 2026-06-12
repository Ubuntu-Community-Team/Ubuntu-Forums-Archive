---
title: "Atheros AR8161, cant compile driver.."
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by trout911 on 2013-02-09
OK, Im fairly new to the ubuntu community so bare with me.
I just upgraded motherboards/cpu/ram yesterday and purchased a Gigabyte 78lmt-s2p motherboard. This board has the Atheros AR8161 network controller. I am having the damnest time getting the driver to compile. I have tried multiple tutorials/tips on here and on the askubuntu site. Looks like im going to need some more in-depth help.

If someone is willing to walk through this with me i would appreciate it.

here is where im at as of now..

```
root@office-server:/home/daniel# cd /home/daniel/Desktop/alx
root@office-server:/home/daniel/Desktop/alx# cd compat-wireless-3.6.8-1-snpc
root@office-server:/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpc#./scripts/driver-select alx
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
Backup exists: drivers/net/ethernet/atheros/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/ethernet/broadcom/Makefile.bk
root@office-server:/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpc# make
make -C /lib/modules/3.5.0-23-generic/build M=/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpc modules
make[1]: Entering directory `/lib/modules/3.5.0-23-generic/build'
make[1]: * No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-23-generic/build'
make: * [modules] Error 2
root@office-server:/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpc# sudo make install
Updating Ubuntu's initramfs for 3.5.0-23-generic under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
done

make -C /lib/modules/3.5.0-23-generic/build M=/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpc modules
make[1]: Entering directory `/lib/modules/3.5.0-23-generic/build'
make[1]: * No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-23-generic/build'
make: * [modules] Error 2
root@office-server:/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpc# &#65279;
```

---

### Post by trout911 on 2013-02-09
im just posting the out puts of the various tutorials/fixes that im finding on the web..

```
root@office-server:/home/daniel/Desktop# dpkg -i linux-backports-modules-cw-3.6-3.5.0-18-generic_3.5.0-18.2_amd64.deb
(Reading database ... 203348 files and directories currently installed.)
Preparing to replace linux-backports-modules-cw-3.6-3.5.0-18-generic 3.5.0-18.2 (using linux-backports-modules-cw-3.6-3.5.0-18-generic_3.5.0-18.2_amd64.deb) ...
Unpacking replacement linux-backports-modules-cw-3.6-3.5.0-18-generic ...
Setting up linux-backports-modules-cw-3.6-3.5.0-18-generic (3.5.0-18.2) ...
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic
root@office-server:/home/daniel/Desktop# sudo modprobe alx
FATAL: Module alx not found.

```

---

### Post by ahallubuntu on 2013-02-09
~

---

### Post by trout911 on 2013-02-09
```
daniel@office-server:~$ sudo apt-get install build-essential
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia firefox-locale-zh-hans k3b k3b-data k3b-i18n
  kde-l10n-engb kde-l10n-zhcn kdevelop-l10n kdevelop-php-docs-l10n
  kdevelop-php-l10n language-pack-kde-en libflac++6 libk3b6 libkcddb4
  linux-headers-3.5.0-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
root@office-server:/home/daniel# cd /home/daniel/Desktop
root@office-server:/home/daniel/Desktop# dpkg -i linux-backports-modules-cw-3.6-3.5.0-18-generic_3.5.0-18.2_amd64.deb
(Reading database ... 203348 files and directories currently installed.)
Preparing to replace linux-backports-modules-cw-3.6-3.5.0-18-generic 3.5.0-18.2 (using linux-backports-modules-cw-3.6-3.5.0-18-generic_3.5.0-18.2_amd64.deb) ...
Unpacking replacement linux-backports-modules-cw-3.6-3.5.0-18-generic ...
Setting up linux-backports-modules-cw-3.6-3.5.0-18-generic (3.5.0-18.2) ...
update-initramfs: Generating /boot/initrd.img-3.5.0-18-generic
root@office-server:/home/daniel/Desktop# sudo modprobe alx
FATAL: Module alx not found.
```

---

### Post by trout911 on 2013-02-09
I have to be doing something wrong. Is that even the right .deb that I should be using?

---

### Post by praseodym on 2013-02-09
You need **3.5.0-23-generic**

---

### Post by chili555 on 2013-02-09
> root@office-server:/home/daniel/Desktop/alx/compat-wireless-3.6.8-1-snpcI suggest you try this again after you have build-essential *and linux-headers-generic* installed:```
./scripts/driver-select restore
./scripts/driver-select alx
make clean
make
make install
modprobe alx
exit
```

---

### Post by trout911 on 2013-02-09
I got it fixed..

Thanks!

---


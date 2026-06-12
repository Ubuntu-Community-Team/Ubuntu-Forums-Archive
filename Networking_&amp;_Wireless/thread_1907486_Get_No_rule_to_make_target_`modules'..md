---
title: "Get No rule to make target `modules'."
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by ztMAMOHT on 2012-01-11
Try to compile [driver]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2722")(Linux driver for kernel 2.6.24 (and later, up to 3.2.x)) for RTL8188CE wirelees card and get error: "make[1]: *** No rule to make target `modules'.  Stop." 

Some information:

```

uname -r
3.0.0-14-generic

lib/modules/3.0.0-14-generic/build$ ls
linux linux-headers-3.0.0-14 linux-headers-3.0.0-14-generic

/usr/src$ ls
linux linux-headers-3.0.0-14 linux-headers-3.0.0-14-generic

Driver downloaded and extracted to "downloads" folder (~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$)
~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# ls
 base.c cam.h compat-wireless-3.0-2.tar.bz2 debug.c efuse.h Makefile ps.c rc.h regd.h rtl8192de stats.h
 base.h compat core.c debug.h firmware pci.c ps.h readme release_note rtl8192se wifi.h
 cam.c compat.h core.h efuse.c Kconfig pci.h rc.c regd.c rtl8192ce stats.c

dpkg -s build-essential
Package: build-essential
Status: install ok installed
...

dpkg -s linux-headers-generic
Package: linux-headers-generic
Status: install ok installed
...

dpkg -s linux-headers-`uname -r`
Package: linux-headers-3.0.0-14-generic
Status: install ok installed
...

```

---

### Post by praseodym on 2012-01-11
Try this version:

[http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#rtl8192de-ce-se-Kombipaket](http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#rtl8192de-ce-se-Kombipaket)

Reboot after that

---

### Post by chili555 on 2012-01-11
His make says:> code-priest@AdeptusComputerus:~$ cd Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/
code-priest@AdeptusComputerus:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$ sudo su
[sudo] password for code-priest:
root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/3.0.0-14-generic/build M=/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: [COLOR="Red"]Entering directory `/lib/modules/3.0.0-14-generic/build'[/COLOR]
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-14-generic/build'
make: *** [all] Error 2My make, with the same driver version and kernel says:> root@LAPTOP60:/home/chili/Desktop/Forum/ztM/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/3.0.0-14-generic/build M=/home/chili/Desktop/Forum/ztM/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: [COLOR="Red"]Entering directory `/usr/src/linux-headers-3.0.0-14-generic'[/COLOR]
  CC [M]  /home/chili/Desktop/Forum/ztM/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/base.o
  CC [M]  /home/chili/Desktop/Forum/ztM/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rc.o
  CC [M]  /home/chili/Desktop/Forum/ztM/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/debug.o
  CC [M]  /home/chili/Desktop/Forum/ztM/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/regd.o
<snip>I don't know why his doesn't recognize the properly installed headers.

Did you make any changes to the Makefile? Will you try:```
cd Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
```Does it still error out?

---

### Post by ztMAMOHT on 2012-01-11
> **chili555 said:**
> His make says:My make, with the same driver version and kernel says:I don't know why his doesn't recognize the properly installed headers.

Did you make any changes to the Makefile? Will you try:```
cd Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
```Does it still error out?

I don't change Makefile. make clean I already try. but with no result.
```
root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Entering directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make[1]: Entering directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make[1]: Entering directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/3.0.0-14-generic/build M=/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/lib/modules/3.0.0-14-generic/build'                                                                                                                               
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-14-generic/build'
make: *** [all] Error 2

```

---

### Post by ztMAMOHT on 2012-01-11
```

reboot was here.

sudo dkms build -m rtl8192ce -v 2.6.0006.0321 --kernelsourcedir /usr/src/linux-headers-3.0.0-14-generic/
Error! Your kernel headers for kernel 3.0.0-14-generic cannot be found.
Please install the linux-headers-3.0.0-14-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# dpkg -s linux-headers-3.0.0-14-generic
Package: linux-headers-3.0.0-14-generic
Status: install ok installed

```
It becomes funny.:P

---

### Post by chili555 on 2012-01-12
Please try:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```As a matter of education, if you can't compile this by hand because of errors, you won't be able to build a dkms because of the very same errors. 

Please try again after the reinstall and let us hear your report.

---

### Post by ztMAMOHT on 2012-01-12
> **chili555 said:**
> Please try:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```As a matter of education, if you can't compile this by hand because of errors, you won't be able to build a dkms because of the very same errors. 

Please try again after the reinstall and let us hear your report.

```
[COLOR="Red"]code-priest@AdeptusComputerus:~$ sudo apt-get install --reinstall linux-headers-generic[/COLOR]
[sudo] password for code-priest: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/2,448 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 110081 files and directories currently installed.)
Preparing to replace linux-headers-generic 3.0.0.14.16 (using .../linux-headers-generic_3.0.0.14.16_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-headers-generic (3.0.0.14.16) ...
[COLOR="red"]code-priest@AdeptusComputerus:~$ sudo apt-get install --reinstall linux-headers-`uname -r`[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/845 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 110081 files and directories currently installed.)
Preparing to replace linux-headers-3.0.0-14-generic 3.0.0-14.23 (using .../linux-headers-3.0.0-14-generic_3.0.0-14.23_i386.deb) ...
Unpacking replacement linux-headers-3.0.0-14-generic ...
Setting up linux-headers-3.0.0-14-generic (3.0.0-14.23) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
Error! Your kernel headers for kernel 3.0.0-14-generic cannot be found.
Please install the linux-headers-3.0.0-14-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
[COLOR="red"]code-priest@AdeptusComputerus:~$ sudo apt-get install linux-headers-`uname -r`[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR="red"]code-priest@AdeptusComputerus:~$ sudo apt-get install linux-headers-3.0.0-14-generic[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-14-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
code-priest@AdeptusComputerus:~$ 
```

---

### Post by chili555 on 2012-01-12
> run-parts: executing /etc/kernel/header_postinst.d/[COLOR="Red"]dkms[/COLOR] 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
Error! Your kernel headers for kernel 3.0.0-14-generic cannot be found.
Please install the linux-headers-3.0.0-14-generic package,
or use the --kernelsourcedir option to tell [COLOR="Red"]DKMS[/COLOR] where it's locatedNow we're getting somewhere! Please try:```
sudo apt-get remove --purge dkms
sudo rm -rf /var/lib/dkms
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install -y dkms
```Then, if everyone is happy, try the 'make' again.

---

### Post by ztMAMOHT on 2012-01-12
> **chili555 said:**
> Now we're getting somewhere! Please try:```
sudo apt-get remove --purge dkms
sudo rm -rf /var/lib/dkms
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install -y dkms
```Then, if everyone is happy, try the 'make' again.

```
code-priest@AdeptusComputerus:~$ sudo apt-get remove --purge dkms
[sudo] password for code-priest: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 467 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110080 files and directories currently installed.)
Removing dkms ...
Purging configuration files for dkms ...
dpkg: warning: while removing dkms, directory '/var/lib/dkms' not empty so not removed.
Processing triggers for man-db ...
code-priest@AdeptusComputerus:~$ sudo rm -rf /var/lib/dkms
code-priest@AdeptusComputerus:~$ sudo apt-get install --reinstall linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/2,448 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 110035 files and directories currently installed.)
Preparing to replace linux-headers-generic 3.0.0.14.16 (using .../linux-headers-generic_3.0.0.14.16_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-headers-generic (3.0.0.14.16) ...
code-priest@AdeptusComputerus:~$ sudo apt-get install --reinstall linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/845 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 110035 files and directories currently installed.)
Preparing to replace linux-headers-3.0.0-14-generic 3.0.0-14.23 (using .../linux-headers-3.0.0-14-generic_3.0.0-14.23_i386.deb) ...
Unpacking replacement linux-headers-3.0.0-14-generic ...
Setting up linux-headers-3.0.0-14-generic (3.0.0-14.23) ...
code-priest@AdeptusComputerus:~$ sudo apt-get install -y dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/72.3 kB of archives.
After this operation, 467 kB of additional disk space will be used.
Selecting previously deselected package dkms.
(Reading database ... 110035 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
code-priest@AdeptusComputerus:~$ cd Downloads/
rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/ Supernatural.s07e11.rus.LostFilm.TV/
code-priest@AdeptusComputerus:~$ cd Downloads/
rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/ Supernatural.s07e11.rus.LostFilm.TV/
code-priest@AdeptusComputerus:~$ cd Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/
code-priest@AdeptusComputerus:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$ sudo su
root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Entering directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192ce'
make[1]: Entering directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192se'
make[1]: Entering directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/rtl8192de'
root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/3.0.0-14-generic/build M=/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make[1]: Entering directory `/lib/modules/3.0.0-14-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-14-generic/build'
make: *** [all] Error 2
root@AdeptusComputerus:/home/code-priest/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# 

```

---

### Post by chili555 on 2012-01-12
I am back to wonering if the Makefile is somehow corrupted. Please post:```
cd Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/
md5sum Makefile
```Mine looks like this:```
md5sum Makefile
[COLOR="Red"]8fbfe6a38e8139265aff5b7fa0526575[/COLOR]  Makefile
```I am running low on ideas. Everything looks perfect...except it isn't.

---

### Post by ztMAMOHT on 2012-01-16
> **chili555 said:**
> I am back to wonering if the Makefile is somehow corrupted. Please post:```
cd Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011/
md5sum Makefile
```Mine looks like this:```
md5sum Makefile
[COLOR="Red"]8fbfe6a38e8139265aff5b7fa0526575[/COLOR]  Makefile
```I am running low on ideas. Everything looks perfect...except it isn't.

```
code-priest@AdeptusComputerus:~/Downloads/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011$ md5sum Makefile 
8fbfe6a38e8139265aff5b7fa0526575  Makefile

```

---

### Post by chili555 on 2012-01-16
Sorry; I am out of ideas/mojo/talent. Do you want to try troubleshooting the built-in module?

---

### Post by ztMAMOHT on 2012-01-16
chili555 thank you for your patience and help. I will use build-in module.

---


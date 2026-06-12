---
title: "RTL8723AS-VAU on Lenovo Yoga 13"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by themanhimself on 2013-05-27
Hi,
I'm an absolute beginner. I have some command of the terminal (pun intended) but I'm not quite sure how to install a driver necessary for the wifi card in my Lenovo Yoga 13. I'm following these instructions ([http://wiki.debian.org/InstallingDebianOn/Lenovo/IdeaPad%20Yoga%2013%20%28wheezy%29](http://wiki.debian.org/InstallingDebianOn/Lenovo/IdeaPad%20Yoga%2013%20%28wheezy%29)) with the RTL8723AS-VAU driver I downloaded. I did a CD to the folder and then the command .make_drv. Here's the transcript
```
luke@luke-Yoga:~$ cd '/home/luke/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224' 
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ ./make_drv
Please select card type(1/2):
1) RTL8723as-vau
2) RTL8723as
#? 1
You have selected RTL8723as-vau
rtw_version.h has existed!
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ make
cp: target ‘driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/autoconf.h’ is not a directory
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/luke/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
/usr/src/linux-headers-3.8.0-19-generic/arch/x86/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target `linux'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Error 2
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ sudo make install
[sudo] password for luke: 
cp: target ‘driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/autoconf.h’ is not a directory
install -p -m 644 8723au.ko  /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install: cannot stat ‘8723au.ko’: No such file or directory
make: *** [install] Error 1


```
I don't know what 'rtw_version.h has existed!' means and there seem to be some errors in there too. Also, after doing this the wifi doesn't work so obviously that's indicative of a problem. Any help would be much appreciated!

---

### Post by chili555 on 2013-05-27
Do you have build-essential installed? Please do so and try again:```
sudo apt-get install build-essential
cd '/home/luke/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224'
make clean [COLOR="#FF0000"]<--may not succeed; please proceed[/COLOR]
./make_drv
```When you see this:> make[1]: *** No rule to make target `linux'.  [COLOR="#FF0000"]Stop.[/COLOR]It means, in human terms: 'Stop as all further steps will be errors and not produce a working driver. Please consult the forum immediately and see if chili555 can help.'

Just for fun, let's confirm your wireless card details:```
lsb_release -d
arch
lspci -nn | grep 0280
```

---

### Post by themanhimself on 2013-05-27
Hi, so I did the first part and got this:
```
luke@luke-Yoga:~$ sudo apt-get install build-essential[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg
  libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6 MB of archives.
After this operation, 29.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main libstdc++6-4.7-dev amd64 4.7.3-1ubuntu1 [1,704 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring/main g++-4.7 amd64 4.7.3-1ubuntu1 [7,993 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring/main g++ amd64 4:4.7.3-1ubuntu10 [1,448 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ raring/main dpkg-dev all 1.16.10ubuntu1 [712 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ raring/main build-essential amd64 11.6ubuntu4 [5,672 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ raring/main fakeroot amd64 1.18.4-2ubuntu1 [89.1 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-diff-perl all 1.19.02-3 [50.0 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12.5 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ raring/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 10.6 MB in 32s (326 kB/s)                                              
Selecting previously unselected package libstdc++6-4.7-dev:amd64.
(Reading database ... 187073 files and directories currently installed.)
Unpacking libstdc++6-4.7-dev:amd64 (from .../libstdc++6-4.7-dev_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.3-1ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.3-1ubuntu10_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.10ubuntu1_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.6ubuntu4_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-3_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Setting up libstdc++6-4.7-dev:amd64 (4.7.3-1ubuntu1) ...
Setting up g++-4.7 (4.7.3-1ubuntu1) ...
Setting up g++ (4:4.7.3-1ubuntu10) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up dpkg-dev (1.16.10ubuntu1) ...
Setting up build-essential (11.6ubuntu4) ...
Setting up fakeroot (1.18.4-2ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
luke@luke-Yoga:~$ cd '/home/luke/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224'
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ make clean
cp: target &#8216;driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/autoconf.h&#8217; is not a directory
cd hal/OUTSRC/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8723a/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/rtl8723a ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal/OUTSRC/rtl8723a ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ ./make_drv
Please select card type(1/2):
1) RTL8723as-vau
2) RTL8723as
#? 1
You have selected RTL8723as-vau
rtw_version.h has existed!
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ make
cp: target &#8216;driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/autoconf.h&#8217; is not a directory
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-22-generic/build M=/home/luke/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224  modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-22-generic'
/usr/src/linux-headers-3.8.0-22-generic/arch/x86/Makefile:103: CONFIG_X86_X32 enabled but no binutils support
make[1]: *** No rule to make target `linux'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-22-generic'
make: *** [modules] Error 2
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ sudo make install
cp: target &#8216;driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224/include/autoconf.h&#8217; is not a directory
install -p -m 644 8723au.ko  /lib/modules/3.8.0-22-generic/kernel/drivers/net/wireless/
install: cannot stat &#8216;8723au.ko&#8217;: No such file or directory
make: *** [install] Error 1
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ 



```
I never got that error you mentioned but I ran the code to confirm the wireless details and got this:
```
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ lsb_release -dDescription:    Ubuntu 13.04
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ arch
x86_64
luke@luke-Yoga:~/Desktop/RTL8723AS-VAU linux driver/rtl8723A_WiFi_linux_v4.1.3_6044.20121224$ lspci -nn | grep 0280



```
So what would you recommend next? Thanks for the help so far!

---

### Post by chili555 on 2013-05-27
You got no reply to lspci; that implies you have *no* PCI wireless device! Let's dig deeper:```
sudo lshw -C network
lsusb
```Fascinating!

---

### Post by themanhimself on 2013-05-27
Ok, I got this:
```
luke@luke-Yoga:~$ sudo lshw -C network  *-network               
       description: Ethernet interface
       physical id: 1
       bus info: usb@3:2
       logical name: eth0
       serial: aa:fa:d8:26:29:4f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth ip=192.168.20.2 link=yes multicast=yes
luke@luke-Yoga:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 05ac:12a0 Apple, Inc. iPhone 4S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 04f3:000a Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 

```

---

### Post by chili555 on 2013-05-27
> ID [COLOR="#FF0000"]0bda:1724[/COLOR] Realtek Semiconductor Corp. There we go! It's evidently a device attached internally to a USB bus. It is, according to many Google hits, an 8723au device. I suspect the driver you have is too old for kernel version 3.8 or may not be suitable for 64-bit. 

I am still working through this promising thread: [http://www.serverphorums.com/read.php?12,681196](http://www.serverphorums.com/read.php?12,681196)

Please try:```
sudo apt-get install git
git clone http://github.com/lwfinger/rtl8723au.git
cd rtl8723au
make
sudo make install
sudo modprobe 8723au
```It makes perfectly on my 3.8.0-xx kernel 64-bit system.

---

### Post by themanhimself on 2013-05-27
You are my hero!!! It worked perfectly! Thanks so much! I'll change the prefix to solved, is there a way to make this accessible to others who may need help?

---

### Post by chili555 on 2013-05-27
Marking it Solved will do it.

When a newer kernel version is installed by Update Manager, recompile after your reboot to the later version:```
cd rtl8723au
make clean
make
sudo make install
sudo modprobe 8723au
```Glad it's working!

---

### Post by themanhimself on 2013-05-31
Thanks for posting that last part. I guess the kernel updated this morning and when I logged back on the wifi wasn't working. Did what you said and it was back up in five minutes!

---

### Post by chili555 on 2013-05-31
Please retain these instructions and the source files for just such cases. I assume it will be included in the mainline kernel at some point. As well, I assume the git version will be updated; I suggest you use what you have for the time being. If it ceases to work in some future kernel, try downloading a current version from git as above and try again.

---


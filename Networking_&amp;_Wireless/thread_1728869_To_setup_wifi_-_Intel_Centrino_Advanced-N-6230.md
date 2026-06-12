---
title: "To setup wifi - Intel Centrino Advanced-N-6230"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by maxim13 on 2011-04-14
I am beginner in Ubuntu. I would like to setup wifi. My laptop is:   
Dell - XPS15, wifi -  Intel Centrino Advanced-N-6230 . 
I tried ndiswrapper  - doesn’t work.  I downloaded driver iwlwifi-6000g2b-ucode-17.16ac8.5.2 and copied one to /lib/firmware … but without any results. For Windows - all ok! 
Thanks!!! 
 
Responses on command: 
[HTML]sudo lshw -c network 
  *-network UNCLAIMED      
       description: Network controller 
       product: Intel Corporation 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 34 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:f1b00000-f1b01fff 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 06 
       serial: 14:fe:b5:98:fa:b9 
       size: 1GB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=1GB/s 
       resources: irq:48 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff 
--------------------------- 
sudo ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 14:fe:b5:98:fa:b9   
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::16fe:b5ff:fe98:fab9/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:4399 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3755 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:4053496 (4.0 MB)  TX bytes:550413 (550.4 KB) 
          Interrupt:48  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 
------------------------------- 
sudo iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
--------------------- 
sudo iwlist wlan0 scan 
wlan0     Interface doesn't support scanning. 
 
sudo apt-get install linux-backports-modules-wireless-maverick-generic 
[sudo] password for maxim:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following extra packages will be installed: 
  linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic 
The following NEW packages will be installed: 
  linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic 
  linux-backports-modules-wireless-maverick-generic 
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded. 
Need to get 2,617kB of archives. 
After this operation, 9,806kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic amd64 2.6.35-28.19 [2,611kB] 
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-backports-modules-wireless-maverick-generic amd64 2.6.35.28.36 [5,528B] 
Fetched 2,617kB in 5s (483kB/s)                                          
Selecting previously deselected package linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic. 
(Reading database ... 145966 files and directories currently installed.) 
Unpacking linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic (from .../linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic_2.6.35-28.19_amd64.deb) ... 
Selecting previously deselected package linux-backports-modules-wireless-maverick-generic. 
Unpacking linux-backports-modules-wireless-maverick-generic (from .../linux-backports-modules-wireless-maverick-generic_2.6.35.28.36_amd64.deb) ... 
Setting up linux-backports-modules-compat-wireless-2.6.36-2.6.35-28-generic (2.6.35-28.19) ... 
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic 
Warning: No support for locale: en_US.utf8 
Setting up linux-backports-modules-wireless-maverick-generic (2.6.35.28.36) ... 
N: Ignoring file 'medibuntu' in directory '/etc/apt/sources.list.d/' as it has no filename extension [/HTML]

---

### Post by maxim13 on 2011-04-15
Please help me!
I really need to setup wifi on Ubuntu.
Thanks!

---

### Post by chili555 on 2011-04-15
Please open a terminal and run and post:```
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by maxim13 on 2011-04-15
> **chili555 said:**
> Please open a terminal and run and post:```
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

Thank you for the response! 



[HTML]maxim@ubuntu:~$ sudo modprobe iwlagn
maxim@ubuntu:~$ dmesg | grep iwl
[  232.869736] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  232.869738] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  232.869835] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  232.869873] iwlagn 0000:03:00.0: setting latency timer to 64
[  232.870026] iwlagn 0000:03:00.0: Detected 6000 Series 2x2 AGN Gen2b, REV=0xB0
[  232.885732] iwlagn 0000:03:00.0: device EEPROM VER=0x716, CALIB=0x6
[  232.885746] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  232.885874] iwlagn 0000:03:00.0: irq 52 for MSI/MSI-X
[  232.913497] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2b-4.ucode' failed.
[  232.913501] iwlagn 0000:03:00.0: no suitable firmware found!
[  232.913746] iwlagn 0000:03:00.0: PCI INT A disabled
 [/HTML]

---

### Post by chili555 on 2011-04-15
> request for firmware file 'iwlwifi-[COLOR="Red"]**6000g2b-4**[/COLOR].ucode'Please post:```
ls -al /lib/firmware | grep ucode
```Thanks.

---

### Post by maxim13 on 2011-04-15
> **chili555 said:**
> Please post:```
ls -al /lib/firmware | grep ucode
```Thanks.


[HTML]  ls -al /lib/firmware | grep ucode
-rw-r--r--  1 root root  335056 2010-12-13 15:01 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-13 15:01 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-13 15:01 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-13 15:01 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-13 15:01 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2010-12-13 15:01 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 2010-12-13 15:01 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 09:20 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-10 13:48 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-02-11 09:17 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 11:18 iwlwifi-6050-5.ucode
maxim@ubuntu:~$ 

[/HTML]
Do I need exactly "iwlwifi-6000g2b-4.ucode"

---

### Post by chili555 on 2011-04-15
> Do I need exactly "iwlwifi-6000g2b-4.ucode"Yes, indeed. Is it in the package you downloaded? Can you move it over to /lib/firmware?

---

### Post by maxim13 on 2011-04-15
> **chili555 said:**
> Yes, indeed. Is it in the package you downloaded? Can you move it over to /lib/firmware?

Unfortunately I have no this file.
Where can I find it?

Here
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)
only 5's version.

Thanks!!!

---

### Post by chili555 on 2011-04-15
I'm googling and suggest you do the same. I am off to dinner with Mrs. Chili. See you later.

---

### Post by maxim13 on 2011-04-15
> **chili555 said:**
> I'm googling and suggest you do the same. I am off to dinner with Mrs. Chili. See you later.

Good luck and thanks!

---

### Post by bkratz on 2011-04-15
> **chili555 said:**
> I'm googling and suggest you do the same. I am off to dinner with Mrs. Chili. See you later.

Dr C. this may be the file--not sure, but it seems to be the older version, hopefully. Please do not use until Chili555 sees it!

[http://intellinuxwireless.org/?n=downloads&f=ucodes_6000g2b](http://intellinuxwireless.org/?n=downloads&f=ucodes_6000g2b)

this was under old releases for g2b5.

Well I guess this is not it. The inside of the file just says  6000-4 ucode not g2b. Sorry.

---

### Post by jawilljr on 2011-04-15
Why not do what [Intel Linux Wireless says]("http://intellinuxwireless.org/?p=iwlwifi")

> 
** Using kernels 2.6.24 and up **

 These kernels have the iwlwifi driver included and the released drivers (available from this site under [download page]("http://intellinuxwireless.org/?n=downloads")) do ** not ** work with these kernels. If you want to run the latest (or very close to         it) development code with your kernel then you should use the **[compat-wireless project]("http://linuxwireless.org/en/users/Download")** that retrieves the latest driver development code from the [ upstream repository]("http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git"). We do push our changes to this repository very frequently.

Just download, compile, and install the latest stable version of compat-wireless.

Jerry

---

### Post by chili555 on 2011-04-15
My firmware files are the same as yours. I assume the version of the driver I have is the same:```
modinfo iwlagn
```> filename:       /lib/modules/2.6.35-28-generic/updates/[COLOR="Red"]compat-wireless-2.6.37[/COLOR]/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux

---

### Post by Amp1776 on 2011-04-15
I have been using ubuntu for several months and went though the same issues, 

I sorted it out with Ath9k.

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)


Download, click on the file to install, the find the tool in system tools to insall driver if it is included. may want to check the list first, but MANY are included.

---

### Post by romer3r on 2011-11-15
I have the same problem with wifi card, idont see the eth1 ethernet interface

I don't see the quest for firmware file 'iwlwifi-6000g2b-4.ucode' failed.

I have few files on lib/firmware/*.ucode

What i can do next to have the wifi working ??
I have a vostro v131 WIFI Intel Centrino Advanced-N 6230

rrustrian@CTimLap-V131:~$ sudo modprobe iwlagn
rrustrian@CTimLap-V131:~$ dmesg | grep iwl
[  113.544534] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  113.544537] iwlagn: Copyright(c) 2003-2010 Intel Corporation



rrustrian@CTimLap-V131:~$ ls -al /lib/firmware | grep ucode
-rw-r--r--  1 root root  335056 2010-12-13 14:01 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-13 14:01 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-13 14:01 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-13 14:01 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-13 14:01 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  340696 2011-03-03 10:08 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 2010-12-13 14:01 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 2010-12-13 14:01 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 08:20 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 08:20 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-02-11 08:17 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 10:18 iwlwifi-6050-5.ucode

Regards

---

### Post by chili555 on 2011-11-16
> **romer3r said:**
> I have the same problem with wifi card, idont see the eth1 ethernet interface

I don't see the quest for firmware file 'iwlwifi-6000g2b-4.ucode' failed.

I have few files on lib/firmware/*.ucode

What i can do next to have the wifi working ??
I have a vostro v131 WIFI Intel Centrino Advanced-N 6230Please reboot so that we have a clean slate and run and post:```
lspci -nn | grep 0280
dmesg | grep iwl
```Thanks.

---

### Post by romer3r on 2011-11-30
To fix my WIFI problem i just install kernel 2.6.39 on ubuntu 10.10 you need to download 3 files and install in the following order:
  1 linux-headers-2.6.39-020639_2.6.39-020639.201105190911_all.deb
  2 linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
  3 linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

you can download from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/) just select the right files for you processor 32 or 64 bits.

Reboot and verify with $ uname -r to see linux kernel version on your terminal

Regards
Romer3R

---

### Post by clownzfu on 2012-10-30
> **romer3r said:**
> To fix my WIFI problem i just install kernel 2.6.39 on ubuntu 10.10 you need to download 3 files and install in the following order:
  1 linux-headers-2.6.39-020639_2.6.39-020639.201105190911_all.deb
  2 linux-headers-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb
  3 linux-image-2.6.39-020639-generic_2.6.39-020639.201105190911_amd64.deb

you can download from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39-oneiric/") just select the right files for you processor 32 or 64 bits.

Reboot and verify with $ uname -r to see linux kernel version on your terminal

Regards
Romer3R

OMFG thanks dude i have been Googling for hours and hours its 430 in the morning and have been at this since ohh the night before last!!!!!! Your a life saver my Distro is Blackbuntu 0.3 and its based off ubuntu 10.10 And the wireless blows LMFAO Thanks I joined the ubuntu forums just to thank you!!!

---


---
title: "Working Broadcom wireless!!"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by indus_credo on 2011-05-04
***This is a how-to on compiling the latest Broadcom driver for people who's card is not working/supported by the driver in repositories***

Hi guys

I just bought a Lenovo Thinkpad E420 some days back. It came pre-installed with Windows 7. So, I chucked that out and installed Ubuntu 11.04 (though I must add I still use in under Gnome classic). But after installation, like most other Linux users, I had a nightmare and the wireless was not working. Right clicking wouldn't be given me an option to 'Enable Wireless'. I tried every single solution on this forum:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

but only to get more frustrated. Weird results as of some commands which I would like to share:

```
kamal@ThinkPad-E420 ~ $lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.7 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 8 [8086:1c1e] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:00.0 System peripheral [0880]: Ricoh Co Ltd Device [1180:e823] (rev 04)
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:0576] (rev 01)
``````
kamal@ThinkPad-E420 ~ $ sudo lshw -C network
[sudo] password for kamal: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:53:f8:6d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:4000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: ac:81:12:20:ca:05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:d1d00000-d1d03fff
```So, coming to the point I thought I should start a thread for people who are struggling with Broadcom drivers for wireless.

To tell you the truth, I only followed the instructions on the Broadcom drivers website which is at 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

But I would like to give step by step instructions for people who might have had difficulty following the readme file

1. ```
sudo apt-get install build-essentials linux-headers-generic
```2. ```
sudo apt-get build-dep linux
```These 2 steps are required to install the relevant headers and tools
Step 2 might return an error regarding sources.list. Don't worry about it!

3. ```
sudo uname -r
```Note down the kernel version number. I will be required at a later stage to load the driver at boot up

4. Download relevant driver - 32bit or 64bit

5. Make a directory in the home folder using
```
mkdir hybrid_wl
```6. Change directory using
```
cd hybrid_wl
```7. Untar the file to the directory we just created
```
tar xzf <path>/hybrid-portsrc_x86-32_v5.100.82.38.tar.gz
```In my case <path> was home/kamal/Downloads
So I wrote
```

tar xzf home/kamal/Downloads/hy...
```8. Now build the driver as linux loadable kernel moduleh

```
make clean
make
```After the build a wl.ko file will be created in this directory

Now, if you have installed STA or any other Broadcom driver before remove it from Synaptics by searching for 'b43'
For removing STA, use

```

sudo apt-get --purge remove bcmwl-kernel-source
```Then type

```
lsmod  | grep "b43\|ssb\|wl"
```If any of the following are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod wl

Though, as per my understanding, the purge command should remove each and every bit.

9. Then type

```
sudo modprobe lib80211
```If it returns any error, use

```
sudo modprobe ieee80211_crypt_tkip
```
And then

```
insmod wl.ko
```Your wireless should be working now and you can enable it by clicking the nm-applet


**Load Driver at boot time**

Now like a smart-*** I didn't do it at first. :P

Type

```
sudo cp wl.ko /lib/modules/'uname -r'/kernel/drivers/net/wireless

```And then

```
sudo depmod -a
```Now the last command, which was meant to be used in Ubuntu, as per the readme, didn't work for me. I had some syntax error.

You can try it by typing

```
sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done
```What I tried was meant to be for Fedora but worked on my Ubuntu.

```
sudo echo modeprobe wl >> /etc/rc.local
```Now, this one denied me permission when I tried to do it this way. So, I had to log in as root and do the command and it worked. Strange, eh!
Later I realised you can use the root terminal as well to do it. It can be found the applications once you unhide it.

---

### Post by d3v1150m471c on 2011-05-04
```

sudo apt-get install b43-fwcutter

```

You may need to remove your old driver first, but that worked for me on my broadcom wireless device.

---

### Post by josephmills on 2011-05-04
> **d3v1150m471c said:**
> ```

sudo apt-get install b43-fwcutter

```

You may need to remove your old driver first, but that worked for me on my broadcom wireless device.

card =14e4:0576
b43 = no
?
?
?
alt=wl
please see 
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by indus_credo on 2011-05-05
> **d3v1150m471c said:**
> ```

sudo apt-get install b43-fwcutter

```

You may need to remove your old driver first, but that worked for me on my broadcom wireless device.

There is no support for my card using b43. So, I had to compile the latest driver from broadcom.

---

### Post by erans on 2011-05-27
I'm having problems with the last part of this. I also have a Thinkpad E420. 

I'm very new to linux and I can't seem to untar the file into the directory. So I extracted the file manually through the GUI and then ran into problems trying to make the driver, so I must have done something wrong. Here are the errors I get: 

```
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ tar xzf home/shayan/Downloads/hybrid-portsrc_x86_64-v5_100_82_38.tar.gz
tar (child): home/shayan/Downloads/hybrid-portsrc_x86_64-v5_100_82_38.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 

```
Then, if I try to manually extract the files through the GUI and make the driver, I get this: 
```
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ make clean
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd` clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CLEAN   /home/shayan/hybrid_wl/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  LD      /home/shayan/hybrid_wl/built-in.o
  CC [M]  /home/shayan/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /home/shayan/hybrid_wl/src/wl/sys/wl_linux.o
/home/shayan/hybrid_wl/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/shayan/hybrid_wl/src/wl/sys/wl_linux.c:485:3: error: implicit declaration of function ‘init_MUTEX’
make[2]: *** [/home/shayan/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/shayan/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 

```
Any help would be appreciated. Thanks.

---

### Post by Matador Guardian on 2011-05-27
EDIT: I didn't realize until now that the post before me was the exact same. Sorry.

Hello,
I do fine up until the make clean and make step. I get through make clean but when I do make it says:


> wallace@wallace-HP-Pavilion-dv4-Notebook-PC:~/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
  LD      /home/wallace/hybrid_wl/built-in.o
  CC [M]  /home/wallace/hybrid_wl/src/shared/linux_osl.o
  CC [M]  /home/wallace/hybrid_wl/src/wl/sys/wl_linux.o
/home/wallace/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/wallace/hybrid_wl/src/wl/sys/wl_linux.c:485:3: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/home/wallace/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make[1]: *** [_module_/home/wallace/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic-pae'
make: *** [all] Error 2

It doesn't make a wl.ko file.. Any help would be appriciated.

Thanks.

---

### Post by erans on 2011-05-28
I was able to compile the driver through a patch on the Broadcom website. But now I can't install the driver and this is driving me crazy. Here's what's happening: 

```
[CODE]shayan@shayan-ThinkPad-E420:~$ lsmod | grep "b43\|ssb\|wl"
wl                   2568244  0 
lib80211               14991  1 wl
shayan@shayan-ThinkPad-E420:~$ rmmod wl
ERROR: Removing 'wl': Operation not permitted
shayan@shayan-ThinkPad-E420:~$ sudo rmmod wl
shayan@shayan-ThinkPad-E420:~$ lsmod | grep "b43\|ssb\|wl"
shayan@shayan-ThinkPad-E420:~$ sudo -i
root@shayan-ThinkPad-E420:~# rmmod wl
ERROR: Module wl does not exist in /proc/modules
root@shayan-ThinkPad-E420:~# lsmod | grep wl
root@shayan-ThinkPad-E420:~# lsmod | grep "wl"
root@shayan-ThinkPad-E420:~# ezit
No command 'ezit' found, did you mean:
 Command 'edit' from package 'mime-support' (main)
ezit: command not found
root@shayan-ThinkPad-E420:~# exit
logout
shayan@shayan-ThinkPad-E420:~$ sudo modprobe lib80211
[sudo] password for shayan: 
shayan@shayan-ThinkPad-E420:~$ insmod wl,ko
insmod: can't read 'wl,ko': No such file or directory
shayan@shayan-ThinkPad-E420:~$ cd hybrid_wl/
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ insmod wl.ko
insmod: error inserting 'wl.ko': -1 Operation not permitted
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 


```[/CODE]
Ugh... any ideas?

---

### Post by Matador Guardian on 2011-05-28
EDIT: You must sudo the insmod command..
```
sudo insmod wl.ko
```

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

erans, your error was that you typed 
```
 insmod wl,ko 
```
instead of
```
insmod wl.ko
```

but it changed it to the correct thing for you and gave you the same error it gave me :/

> wallace@wallace-HP-Pavilion-dv4-Notebook-PC:~/hybrid_wl$ sudo modprobe lib80211
wallace@wallace-HP-Pavilion-dv4-Notebook-PC:~/hybrid_wl$ insmod wl.ko
insmod: error inserting 'wl.ko': -1 Operation not permitted


---

### Post by erans on 2011-05-28
This is what sudo insmod wl.ko is giving me: 
```
shayan@shayan-ThinkPad-E420:~$ cd hybrid_wl/
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ ls
5_100_82_38.patch                          Makefile        wl.ko
built-in.o                                 modules.order   wl.mod.c
hybrid-portsrc_x86_64-v5_100_82_38.tar.gz  Module.symvers  wl.mod.o
lib                                        src             wl.o
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ sudo insmod wl.ko
[sudo] password for shayan: 
insmod: error inserting 'wl.ko': -1 Unknown symbol in module
shayan@shayan-ThinkPad-E420:~/hybrid_wl$ 

```
So I'm not sure at all what this means...

---


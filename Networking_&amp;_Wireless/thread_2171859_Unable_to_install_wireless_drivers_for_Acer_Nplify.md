---
title: "Unable to install wireless drivers for Acer Nplify 802.11b/g/n"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by mrashevski on 2013-09-02
Hello! I am completely new to Linux system (previously using Mac and Windows) and I am struggling with the new interface in order to get my wireless card recognised and working.

Linux version is Ubuntu 12.04, card is Acer Nplify 802.11b/g/n. Additional Drivers option found drivers for my graphic card and even for the wireless (recognised as ) "Broadcom STA proprietary wireless driver" (" This package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware.") 

However, when I try to activate it, after entering the administration password, I get an error massage:

"Sorry, the installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log"

Then I try to open the log file using the terminal (is this the right thing to do?) and I get:

bash: /var/log/jockey.log: Permission denied

I checked some forums, but I didn't get better results. I would appreciate some help for a new user. Thank you in advance!

Milan

---

### Post by varunendra on 2013-09-02
Welcome to the forums mrashevski !

Please open a terminal (Ctrl+Alt+T), enter the following command and post back its output -
```
lspci -nnk | grep -iA2 net
```

This will give us the exact id of your wireless card so we can determine the best driver for it. The one proposed by the "Additional Drivers" application is not always the best.

---

### Post by mrashevski on 2013-09-02
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel modules: bcma
```

I tried to follow the instructions from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers) but there was problem when installing 
bcmwl-kernel-source

[FONT=arial]Thank you for your reply!!!

[/FONT]

---

### Post by varunendra on 2013-09-02
While being connected to internet via cable, please do -
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Post back if there are any errors while executing above. If it went smooth, you should have a working wifi. Reboot if required, and let me know the result.

---

### Post by mrashevski on 2013-09-02
Thank you! I tried this step, but I get problem while installing:

```
First Installation: checking all kernels...
Building only for 3.8.0-29-generic
Building for architecture x86_64
Building initial module for 3.8.0-29-generic
Error! Bad return status for module build on kernel: 3.8.0-29-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
Warning: No support for locale: en_GB.utf8
```

After that it displays a crash report window from Linux - Sorry, a problem ocurred while installing software. 
Under details there is:
Package: bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu0.0.1
ProblemType: Package
...
Architecture: amd64 (my processor is IntelCore i5-2450M, if the x64 system is relevant for the drivers)

It seems that the problem is with bcmwl-kernel-source. I referred to the following link ([https://bugs.launchpad.net/jockey/+bug/989610](https://bugs.launchpad.net/jockey/+bug/989610)) where other people posted the same problem, however, I am still unable to get the card running. Thanks again for your help!

Milan

---

### Post by mrashevski on 2013-09-02
p.s. The log files does not open - 

```
milan@ubuntu:~$ /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log
bash: /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log: Permission denied
```

---

### Post by varunendra on 2013-09-02
The log file is just a text file, not an executable program, hence the last "permission denied" error, which is obvious and not a problem.

Please post its contents, which you can read by normally browsing to the location (/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/) and manually opening it, or -
```
cat /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log
```

Post back the whole log here. Please use 'Code' tags for posting the log (see this post on how to use Code tags) - [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by mrashevski on 2013-09-02
Thanks! I was just wondering how to post the code information in an appropriate format, like the other forums I checked. This is the log file information:

```
milan@ubuntu:~$ cat /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log
DKMS make.log for bcmwl-6.20.155.1+bdcom for kernel 3.8.0-29-generic (x86_64)
Mon Sep  2 15:04:36 JST 2013
make: Entering directory `/usr/src/linux-headers-3.8.0-29-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_linux.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_iw.o
  CC [M]  /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function ‘wl_cfg80211_join_ibss’:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:705:26: error: ‘struct cfg80211_ibss_params’ has no member named ‘channel’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: At top level:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: initialisation from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1560:2: warning: (near initialisation for ‘wl_cfg80211_ops.scan’) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: initialisation from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1565:2: warning: (near initialisation for ‘wl_cfg80211_ops.set_tx_power’) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: initialisation from incompatible pointer type [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1566:2: warning: (near initialisation for ‘wl_cfg80211_ops.get_tx_power’) [enabled by default]
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c: In function ‘wl_update_bss_info’:
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1991:11: error: ‘struct cfg80211_bss’ has no member named ‘information_elements’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1992:15: error: ‘struct cfg80211_bss’ has no member named ‘len_information_elements’
make[1]: *** [/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.8.0-29-generic'

```

---

### Post by mrashevski on 2013-09-02
p.s. 
```
milan@ubuntu:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
milan@ubuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by mrashevski on 2013-09-02
```
milan@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: dc:0e:a1:18:c2:6f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=sb ip=192.168.0.68 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:d1830000-d183ffff memory:d1840000-d184ffff memory:d1850000-d18507ff
  *-network UNCLAIMED
       description: Network controller
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:d1900000-d1903fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

The description of the Broadcam device says just "Netwrok controller" and no "Wireless interface" like it is supposed to be.
I installed Ubuntu, just 2 days ago, previously running Windows 7 with no driver problems for the wireless card. Last to days I try to solve it reading and reading.
In the lab where I work there is no cable connection. Otherwise I wouldn't bother you with the problem. Thanks again for your help!

---

### Post by varunendra on 2013-09-02
> **mrashevski said:**
> ```

/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:705:26: error: ‘struct cfg80211_ibss_params’ has no member named ‘channel’
....
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1991:11: error: ‘struct cfg80211_bss’ has no member named ‘information_elements’
/var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/src/wl/sys/wl_cfg80211.c:1992:15: error: ‘struct cfg80211_bss’ has no member named ‘len_information_elements’

```
Hmm.. evidently, it is a discrepancy in the source code of the driver which I'm not sure I can rectify without a lot of research. However, you can compile the official driver from broadcom's site. Similar discrepancies exist in that one too, but we figured that one out sometime ago.

Please follow the instructions in this post to download and compile the driver : [http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619)

Although the post was written for a different card, hopefully, the same driver should work for you too.

---

### Post by mrashevski on 2013-09-02
Thank you! I almost got it from the link you gave me. Everything except for the last command worked fine:

```
root@ubuntu:/home/milan/Desktop/hybrid-portsrc_x86_64-v5_100_82_112# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
Warning: No support for locale: en_GB.utf8

```

I will check it out once more. Please, tell me if you come up with a solution. Thank you again for your time and efforts!

---

### Post by varunendra on 2013-09-02
You're welcome, and troubleshooting is fun :)

Warnings are okay, as long as they don't lead to 'errors'. Just try the newly installed driver (wl) and if it doesn't behave nicely, follow the "Wireless Script" link in my signature, follow the instructions to run the script and post back the report it generates. Although I hope (with fingers crossed ;)) that you won't need it.

---

### Post by mrashevski on 2013-09-02
Hello, again! The card is Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]. After struggling, installing and uninstalling, my highest progress was to see "Wireless interface" for 5min, until the restart of the computer - new errors and the card was again just "Network controller". I feel a bit stupid and a bit desperate, so if anyone has any suggestions, please help! Should I try older version of Linux?

If somebody experience similar problem, the most useful links are:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers) (general information)
[https://bugs.launchpad.net/jockey/+bug/989610](https://bugs.launchpad.net/jockey/+bug/989610) (steffen and doubi's replies)
[http://ubuntuforums.org/showthread.p...9#post12629619]("http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619")

Well, again - if somebody has time and patience to give a hand to a newcomer, I will appreciate it a lot! Take care!

p.s. thanks a lot to varunendra, who invested so much time this afternoon.

---

### Post by varunendra on 2013-09-02
> **mrashevski said:**
> The card is Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358].
....
...
[https://bugs.launchpad.net/jockey/+bug/989610](https://bugs.launchpad.net/jockey/+bug/989610) (steffen and doubi's replies)
The steffen's suggestion on the bug report page won't work for everyone. There are certain models of broadcom chips that won't work with the suggested b43 driver. Your card is one of them and will only work with the proprietary 'wl' driver. See [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

Even if you try an older version, either it will be outdated (not supported anymore, thus possibly causing different problems) or will be using the same newer version of the kernel which the default driver is having compiling problems with.

Please run the "Wireless Script" (following the link in my signature) and post back its result here. It should be easier to decide the best course of action with the detailed information it will give us.

**PS:**
Hanging out on the forums is the favourite time-pass for many of us (as long as we have time to pass ;)). So no problems there.

---

### Post by gorvatsal2191 on 2013-09-02
I am also strugggling with same problem

---

### Post by mrashevski on 2013-09-02
Hello, everybody! A friend of mine dedicated several hours and solved it, don't ask me exactly how, I was asleep after whole day of struggling. : ) It keeps giving me error to report sometimes, but I just ignore it and use my wireless! The driver installed is this one: [https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504)

So may be it's not for the same chip, but it works for me. I hope a more proper solution would be found soon. Take care and good luck!

---

### Post by varunendra on 2013-09-02
Congratulations !!
> **mrashevski said:**
> The driver installed is this one: [https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504)

So may be it's not for the same chip, but it works for me. I hope a more proper solution would be found soon. Take care and good luck!
It is the same proprietary driver 'wl', only a newer version, perhaps with some modifications in the source code to suite the 64bit kernel.

The package 'bcmwl....' is the name of the source package, the driver it creates is always 'wl.ko' and it is called by the system as just 'wl'. You can use the command - "nm-tool" to confirm that.

Thanks for the link, it is very helpful for both who are looking for help and those of us who try to help. :)
Hopefully, it will make its way in forthcoming updates.

---

### Post by varunendra on 2013-09-02
> **gorvatsal2191 said:**
> I am also strugggling with same problem

Welcome to the forums gorvatsal2191 !!

Wireless issues are very subjective and their reasons as well as solutions can vary from person to person.

So unless you are absolutely sure you have the same card using the same driver (on the same version of Ubuntu), I'd suggest to start your own thread and post the details of your problem.

If you are sure you have the same problem, try the driver that mrashevski linked to in the above post. It is a .deb file, so you can just double-click to install it.

---


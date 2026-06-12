---
title: "Qualcomm Atheros QCA9565/ AR9565, UBUNTU 12.04"
date: 2013-09-03
forum: Networking &amp; Wireless
---

### Post by anoop_n2 on 2013-09-03
I had purchased a **Dell Inspiron 14 3421** LAPTOP,  My WiFi details are
**Qualcomm Atheros QCA 95665/ AR9565 wireless network adapter[168c:0036] (rev 01)**.
I have installed **Ubuntu12.04** LTS , but WiFi driver is not detected.
I had contacted DELL Support center on phone, They had suggested to install 
a genuine Windows version which is only supported by them
Please help me to find out a driver.
Thanks in advance
Anoop

---

### Post by chili555 on 2013-09-03
Please check here: [http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062) Post #1 describes your device, Ubuntu 12.04 and includes the solution.

---

### Post by anoop_n2 on 2013-09-03
It worked like a CHARM
Brief of what i did for further reference.

**sudo apt-get install linux-headers-generic build-essential**

[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/)
Downloaded and extracted; compat-drivers-3.9-rc4-2-s.tar.bz2

[B]cd Desktop/compat-drivers-3.9-rc4-2-s
sudo su
./scripts/driver-select ath9k
make[/B]


I got one error after this command, the error was 
[B]error: redefinition of &#8216;kref_get_unless_zero&#8217;
include/linux/kref.h:47:32: note: previous definition of &#8216;kref_get_unless_zero&#8217; was here[/B]

Then i did this in one of file 

[B]open the file .../compat-wireless-2012-12-18/include/linux/compat-3.8.h in your favourite editor, 
find the kref_get_unless_zero function (telling from your error message, it should be on line 47) and comment it out. In case you have no idea what I'm talking about: Comment this code


static inline int __must_check kref_get_unless_zero(struct kref *kref)
{
        return atomic_add_unless(&kref->refcount, 1, 0);
}
[/B]
then 

carry on with

[B]make
make install
exit[/B]

after a reboot , my wifi is working like a charm.....

Thanks 
Anoop

---

### Post by chili555 on 2013-09-03
Awesome! Great job.  You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile: ```
cd compat-wireless-3.6.6-1-snpc
sudo su
make clean
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit
```The change to compat-3.8.h need not be repeated.

Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by chodislav on 2013-11-06
> **chili555 said:**
> Awesome! Great job.  You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile: ```
cd compat-wireless-3.6.6-1-snpc
sudo su
make clean
./scripts/driver-select ath9k
make
make install
modprobe ath9k
exit
```The change to compat-3.8.h need not be repeated.

Please mark the thread Solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

I have the same problem driver for Qualcomm Atheros QCA9565/ AR9565 is not instaled, but when I perform the quoted commands I get stuck at make command, 

Here the code:
```
choda@Lappy:~$ cd compat-wireless-3.6.6-1-snpc/
choda@Lappy:~/compat-wireless-3.6.6-1-snpc$ sudo su
[sudo] password for choda:
root@Lappy:/home/choda/compat-wireless-3.6.6-1-snpc# make clean
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-55-generic'
  CLEAN   /home/choda/compat-wireless-3.6.6-1-snpc
  CLEAN   /home/choda/compat-wireless-3.6.6-1-snpc/.tmp_versions
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-55-generic'
root@Lappy:/home/choda/compat-wireless-3.6.6-1-snpc# ./scripts/driver-select ath9kProcessing new driver-select request...
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: drivers/net/wireless/ath/Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/bcma/Makefile.bk
Backup exists: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@Lappy:/home/choda/compat-wireless-3.6.6-1-snpc# make
./scripts/gen-compat-autoconf.sh /home/choda/compat-wireless-3.6.6-1-snpc/.config /home/choda/compat-wireless-3.6.6-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-55-generic/build M=/home/choda/compat-wireless-3.6.6-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-55-generic'
  CC [M]  /home/choda/compat-wireless-3.6.6-1-snpc/compat/main.o
In file included from /home/choda/compat-wireless-3.6.6-1-snpc/include/linux/compat-2.6.h:64:0,
                 from <command-line>:0:
/home/choda/compat-wireless-3.6.6-1-snpc/include/linux/compat-3.4.h:32:21: error: redefinition of ‘kmalloc_array’
include/linux/slab.h:243:21: note: previous definition of ‘kmalloc_array’ was here
make[3]: *** [/home/choda/compat-wireless-3.6.6-1-snpc/compat/main.o] Error 1
make[2]: *** [/home/choda/compat-wireless-3.6.6-1-snpc/compat] Error 2
make[1]: *** [_module_/home/choda/compat-wireless-3.6.6-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-55-generic'
make: *** [modules] Error 2
```

This is my first time working in Ubuntu and I'm already stuck

---

### Post by chili555 on 2013-11-06
Would you mind just confirming a few things?```
lspci -nn | grep 0280
sudo dpkg -s build-essential | head -n5
```

---

### Post by chodislav on 2013-11-06
```
choda@Lappy:~$ lspci -nn | grep 0280
08:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)

```

```
choda@Lappy:~$ sudo dpkg -s build-essential | head -n5
[sudo] password for choda:
Package: build-essential
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 37

```

I disabled wireless connection in upper right corner and since then I don't have option to enable it again.

While looking for solution on internet I found this command, maybe it can help..

```
choda@Lappy:~$ sudo lshw -C network
  *-network              
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: 74:86:7a:6c:7e:56
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1500000-c157ffff memory:9fb00000-9fb0ffff
```
Thanks for help :)

---

### Post by chili555 on 2013-11-07
I may have found it! In the changelog for 3.6.[COLOR="#FF0000"]8[/COLOR] here: >  compat: Backport kmalloc_array()Therefor, please try to compile this package instead: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2)

---

### Post by chodislav on 2013-11-07
Nope, that file won't do the trick :(

```

root@Lappy:/home/choda/compat-wireless-3.6.8-1-snpc# make
./scripts/gen-compat-autoconf.sh /home/choda/compat-wireless-3.6.8-1-snpc/.config /home/choda/compat-wireless-3.6.8-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-55-generic/build M=/home/choda/compat-wireless-3.6.8-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-55-generic'
  CC [M]  /home/choda/compat-wireless-3.6.8-1-snpc/compat/main.o
In file included from /home/choda/compat-wireless-3.6.8-1-snpc/include/linux/compat-2.6.h:64:0,
                 from <command-line>:0:
/home/choda/compat-wireless-3.6.8-1-snpc/include/linux/compat-3.4.h:32:21: error: redefinition of ‘kmalloc_array’
include/linux/slab.h:243:21: note: previous definition of ‘kmalloc_array’ was here
make[3]: *** [/home/choda/compat-wireless-3.6.8-1-snpc/compat/main.o] Error 1
make[2]: *** [/home/choda/compat-wireless-3.6.8-1-snpc/compat] Error 2
make[1]: *** [_module_/home/choda/compat-wireless-3.6.8-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-55-generic'
make: *** [modules] Error 2
```

---

### Post by chili555 on 2013-11-07
Greater love for the forum hath no Chili than he installeth 12.04 LTS on an old harddrive and compile the driver. It compiles for me with a couple of warnings and *NO* errors. I am mystified.> chili@ThinkT60:~/Desktop/compat-wireless-3.6.8-1-snpc$ modinfo drivers/net/wireless/ath/ath9k/ath9k.ko
filename:       drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4ADBC452D2F0E3C7755CB89
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]0036[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
<snip>

May I assume you did do this step before you did 'make?'```
./scripts/driver-select ath9k
```If you didn't or you are unsure, please do:```
cd /home/choda/compat-wireless-3.6.8-1-snpc
make clean
./scripts/driver-select ath9k
make
sudo make install
```Weird.

---

### Post by chodislav on 2013-11-07
Yes I did, here's the rest of code:
```
choda@Lappy:~$ cd compat-wireless-3.6.8-1-snpc/
choda@Lappy:~/compat-wireless-3.6.8-1-snpc$ sudo su
[sudo] password for choda:
root@Lappy:/home/choda/compat-wireless-3.6.8-1-snpc# make clean
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-55-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-55-generic'
root@Lappy:/home/choda/compat-wireless-3.6.8-1-snpc# ./scripts//driver-select ath9k
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backing up makefile: drivers/net/wireless/ath/Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/bcma/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
Backup exists: Makefile.bk
root@Lappy:/home/choda/compat-wireless-3.6.8-1-snpc# make
./scripts/gen-compat-autoconf.sh /home/choda/compat-wireless-3.6.8-1-snpc/.config /home/choda/compat-wireless-3.6.8-1-snpc/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-55-generic/build M=/home/choda/compat-wireless-3.6.8-1-snpc modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-55-generic'
  CC [M]  /home/choda/compat-wireless-3.6.8-1-snpc/compat/main.o
In file included from /home/choda/compat-wireless-3.6.8-1-snpc/include/linux/compat-2.6.h:64:0,
                 from <command-line>:0:
/home/choda/compat-wireless-3.6.8-1-snpc/include/linux/compat-3.4.h:32:21: error: redefinition of ‘kmalloc_array’
include/linux/slab.h:243:21: note: previous definition of ‘kmalloc_array’ was here
make[3]: *** [/home/choda/compat-wireless-3.6.8-1-snpc/compat/main.o] Error 1
make[2]: *** [/home/choda/compat-wireless-3.6.8-1-snpc/compat] Error 2
make[1]: *** [_module_/home/choda/compat-wireless-3.6.8-1-snpc] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-55-generic'
make: *** [modules] Error 2
```

If you had no idea what's wrong, no matter, thanks for your time anyway I'm glad to see how this forum works and that there are people who will help you if you have problem. 

I'll reinstall Ubuntu and problem will be solved hopefully, anyhow I learned a lot about Linux during this problem solving and I'm looking forward to discover more and more about Linux.

---

### Post by ravya on 2013-11-12
Thanks a lot Anoop, worked very well for me as well !

---

### Post by saroj-kumar85 on 2013-11-13
Thank You Anoop :)

---

### Post by chili555 on 2013-11-14
> **chodislav said:**
> 
I'll reinstall Ubuntu and problem will be solved hopefully, anyhow I learned a lot about Linux during this problem solving and I'm looking forward to discover more and more about Linux.Can you please try installing a PAE kernel?

---

### Post by npandey057 on 2014-01-01
I got the wireless working by following the instructions. But it is not able to connect or scan the wifi connections available. Other devices are working fine. What should I do?

I am on 12.04 LTS Dell Inspiron 15 3537.

---

### Post by chili555 on 2014-01-01
> **npandey057 said:**
> I got the wireless working by following the instructions. But it is not able to connect or scan the wifi connections available. Other devices are working fine. What should I do?

I am on 12.04 LTS Dell Inspiron 15 3537.Let's have a look at:```
lspci -nn | grep 0280
iwconfig
rfkill list all
```

---

### Post by Modsley on 2014-04-07
Post #3 worked for me. Yet only after removing *backports* package with a driver from repository.

---

### Post by nsdelgadov on 2014-05-24
Muchas gracias, me funcionó :D

**Solved, thanks!**

---

### Post by dhiren2 on 2014-05-27
Thanks you. You are amazing.

---


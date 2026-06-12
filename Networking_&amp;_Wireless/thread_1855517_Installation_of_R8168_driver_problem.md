---
title: "Installation of R8168 driver problem"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by chirag64 on 2011-10-06
I've been having problems on my ubuntu recently. I've not been able to connect to the internet.

A friend of mine suggested that I try to reinstall the drivers, so I removed the old one and tried installing the new ones, but the installation is generating a few errors.
```
chirag@ABC-Chirag:~/Desktop/r8169-6.015.00$ lsmod | grep 816
chirag@ABC-Chirag:~/Desktop/r8169-6.015.00$ sudo make clean modules 
make -C src/ clean
make[1]: Entering directory `/home/chirag/Desktop/r8169-6.015.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset modules.order Module.markers
make[1]: Leaving directory `/home/chirag/Desktop/r8169-6.015.00/src'
make -C src/ modules
make[1]: Entering directory `/home/chirag/Desktop/r8169-6.015.00/src'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/chirag/Desktop/r8169-6.015.00/src'
make: *** [modules] Error 2
chirag@ABC-Chirag:~/Desktop/r8169-6.015.00$ 


```Any ideas what this error means and how I can solve it? I'm not very good with Ubuntu command lines, I've followed these commands as per the README file in the tar file

---

### Post by chili555 on 2011-10-06
> No rule to make target `/src/Makefile'.  Stop.This suggests that the needed build tools may not be installed. Please open Synaptic Package Manager and see if *build-essential* is installed. Can you please install it and try again?

Is this computer dual-booting with Windows? With the ethernet cable plugged in, please run:```
sudo lshw -C network
```Do you get link=no even though the cable is plugged in?> *-network       
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.5-1 latency=0 **[COLOR="Red"]link=no[/COLOR]** multicast=yes port=twisted pair
       resources: irq:48 memory:ee000000-ee01ffff ioport:3000(size=32)

---

### Post by chirag64 on 2011-10-09
OK, this is what I got by using that command:
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:de00(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:fdf00000-fdf0ffff

```

---

### Post by chili555 on 2011-10-09
The needed driver r8169 is already in the kernel. Let's see what happens if we load it manually. Please run and post:```
sudo modprobe r8169
ifconfig
dmesg | grep 8169
```Thanks.

---

### Post by chirag64 on 2011-10-09
```
chirag@ABC-Chirag:~$ sudo modprobe r8169
[sudo] password for chirag: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.bk, it will be ignored in a future release.
FATAL: Module r8169 not found.
chirag@ABC-Chirag:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

chirag@ABC-Chirag:~$ dmesg | grep 8169
chirag@ABC-Chirag:~$ 

```:(

---

### Post by chili555 on 2011-10-10
> FATAL: Module r8169 not found.Interesting. Somebody has been busy here. Did you remove the /lib/modules/etc. line altogether? What caused you to try to build r8168 from source?

Since ethernet is not working, do you have any internet connectivity at all?

---

### Post by chirag64 on 2011-10-10
Yeah, actually I tried a lot of things (that I didn't understand) earlier also to solve this problem :(...

I don't have any net connectivity on my Ubuntu since a few months now

My computer has dual boot...internet works perfectly on Windows 7, but not on Ubuntu :(

---

### Post by chili555 on 2011-10-10
Do you have the install CD that you used to install? Can you run a live CD session and see what this tells us?```
sudo updatedb
locate r8169.ko
sudo modprobe r8169
dmesg | grep 8169
```

---

### Post by praseodym on 2011-10-10
Hi,

the script of the driver renames the module r8169.ko to r8169.bak. Install the driver via:

```
sudo ./autogen.sh
```
in the driver folder.

---

### Post by praseodym on 2011-10-10
P.S.: You are trying to install again the r8169. Use the "right" driver r8168, see here:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Downloadlink:

[http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2)

---

### Post by varunendra on 2011-10-11
> **chili555 said:**
> The needed driver r8169 is already in the kernel.
chili,
Do you think r8169 is good for 8168B controller? Because I have seen many users having issues with this combination (which is default in ubuntu..!). For example these:
[http://ubuntuforums.org/showthread.php?t=1805271&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1805271&highlight=r8168)
[http://ubuntuforums.org/showthread.php?t=1824464&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1824464&highlight=r8168)

However, all those users I have seen did have a connection, just very slow and/or inconsistent. Unless you tell me otherwise, I believe this combination is a no-match at all.

@chirag,
Although the links I have provided also contain a possible solution, the one given by praseodym deals with a newer (and perhaps better) driver. Besides, you are already in hands of best guys here. I just jumped in to clear my doubt about what chili said.

---

### Post by praseodym on 2011-10-11
Hi,

this is why I linked to the r816[COLOR="Red"]8[/COLOR] installation. The thread starter wants to compile the r816[COLOR="Red"]9[/COLOR], which is already part of the kernel.

---

### Post by chili555 on 2011-10-11
> Do you think r8169 is good for 8168B controller?There are as many cases where it works fine and is, in fact, used to post data to solve wireless issues. We see it in lshw. I certainly have seen some problems but not so many that I think it's a notorious non-performer.

It makes sense to install r8168 since he has evidently removed r8169 entirely. He may not yet have *build-essential*.

---

### Post by praseodym on 2011-10-11
> **chili555 said:**
> He may not yet have *build-essential*.

To chirag64:

The packages **dkms** and **build-essential** can be installed from CD, just add it to your software sources. You also need the kernel-headers, if not installed:

```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```
If you update your system to kernel -11, install the metapackage:

```
sudo apt-get install linux-headers-generic
```
Is it 32 or 64 bit?

---

### Post by chirag64 on 2011-10-15
> **chili555 said:**
> Do you have the install CD that you used to install? Can you run a live CD session and see what this tells us?```
sudo updatedb
locate r8169.ko
sudo modprobe r8169
dmesg | grep 8169
```

I had installed using a 10.04 CD and later upgraded it to 11.04 and  thats when the problem started.
Eitherways, I'm using my 10.04 CD as a Live CD and running these....

```
ubuntu@ubuntu:~$ sudo updatedb
ubuntu@ubuntu:~$ locate r8169.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/net/r8169.ko
/rofs/lib/modules/2.6.32-21-generic/kernel/drivers/net/r8169.ko
ubuntu@ubuntu:~$ sudo modprobe r8169
ubuntu@ubuntu:~$ dmesg | grep 8169
[    1.558169] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.067554] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.067566] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.067593] r8169 0000:02:00.0: setting latency timer to 64
[    3.067634] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[   42.487661] r8169: eth0: link up
[   42.487666] r8169: eth0: link up
ubuntu@ubuntu:~$ 

```

Btw, internet runs fine on this 10.04 Live CD

---

### Post by chirag64 on 2011-10-15
> **praseodym said:**
> P.S.: You are trying to install again the r8169. Use the "right" driver r8168, see here:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

Downloadlink:

[http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.025.00.tar.bz2)

I think i've tried this earlier, but somehow failed, thats why I again removed r8168 and downloaded r8169. Lemme try again...

---

### Post by chirag64 on 2011-10-15
Ohk, it looks like I'm back to square one :(

I had planned to remove the drivers and install new ones because my PPPOE connection was not working and my friend told me it was a driver issue.

Now the drivers have been installed properly, but internet connection is still not alive, so I'm not sure if my internet problem is related to the drivers or not.

I start my internet connection using **sudo pppoeconf**, but I keep getting the error:

```
    &#9474; Sorry, I scanned 1 interface, but the Access             &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason for  &#9474; 
          &#9474; the scan failure may also be another running pppoe       &#9474; 
          &#9474; process which controls the modem.         

```

Is there any way that I can know that this is because of my drivers or not?

---


---
title: "Problems Installing NetLink BCM57781 Ethernet Driver"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by 1cube1wheel on 2012-11-29
I have been experiencing problems with my internet on Ubuntu 12.10 (web  pages will randomly be unable to load, internet cuts out and comes  back)  so I thought I would update my ethernet driver.  

I  downloaded the appropriate driver from NetLink but I am having trouble  following their instructions for installation.  After unpacking the .tar  file I am instructed to go to the src folder and run make.  There is no  src folder, so I went into the only folder available after unpacking  the .tar file and ran make, only to receive the following error:

sh makeflags.sh   > tg3_flags.h
makeflags.sh: No kernel source directory provided.
make: *** [tg3_flags.h] Error 255

Anyone know what the problem is?  Thank you.

---

### Post by chili555 on 2012-11-29
Here is a whole thread describing issues installing this module: [http://ubuntuforums.org/showthread.php?t=2078320&page=2](http://ubuntuforums.org/showthread.php?t=2078320&page=2) In post #12, there is a download link. I just downloaded it and compiled it successfully in 12.10. Please download it and install the needed tools:```
sudo apt-get install linux-headers-generic build-essential
```I need to switch locations, but I'll be with you in a few minutes and we'll compile it.

It makes and installs without warning or error. Whether it works better, I don't know. I don't have the hardware.

---

### Post by chili555 on 2012-11-29
Please download the file to your desktop. Right-click and select Extract Here. Open a terminal and do:```
cd Desktop/tg3-3.124c
make
sudo make install
```We will be very interested to hear your experience. Does it solve your instability?

---

### Post by 1cube1wheel on 2012-11-29
After downloading what you suggested in your first post, I tried to run 'make' again and encountered the following error: 

make -C /lib/modules/3.5.0-18-generic/build SUBDIRS=/home/tac/Downloads/Server/Linux/Driver/tg3-3.124c modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-18-generic'
  CC [M]  /home/tac/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.o
/home/tac/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.c:96:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/home/tac/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.o] Error 1
make[1]: *** [_module_/home/tac/Downloads/Server/Linux/Driver/tg3-3.124c] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-18-generic'
make: *** [default] Error 2

This  error looks familiar to something I read in the thread you linked me  to, so I will also check back in there to see if there is a solution to  the problem.  Thanks.

---

### Post by chili555 on 2012-11-29
> /home/tac/Downloads/Server/Linux/Driver/tg3-3.124cYou are in the directory of the *OLD* (read: defective) driver, not the one I linked that you hopefully downloaded to your desktop:> Please download the file to your desktop. Right-click and select Extract Here. Open a terminal and do:
```
cd Desktop/tg3-3.124c
make
sudo make install

```


---

### Post by 1cube1wheel on 2012-11-29
Ohh, my mistake.  I downloaded the copy of the driver you linked me to and it installed just fine.  For now, it seems like my internet is working alright, but I won't know for sure until I have used it for a little longer.  Thanks for your help, and I will post on the thread again if that did not solve my stability issues.

---

### Post by chili555 on 2012-11-29
Please let us know.

Whenever a newer kernel version is installed by Update manager, you'll need to re-compile:```
cd Desktop/tg3-3.124c
make clean
make
sudo make install
```

---

### Post by 1cube1wheel on 2012-11-30
Thanks for the info.  So, I marked this thread as solved earlier because technically the issue was with installing the Ethernet driver, which I was able to do in the end.  However, that did not solve my internet problems.  Still, web pages will random be unable to load, and my connection cuts in and out.  Any ideas as to what may be causing this?  Thanks.

---

### Post by chili555 on 2012-11-30
> **1cube1wheel said:**
> Thanks for the info.  So, I marked this thread as solved earlier because technically the issue was with installing the Ethernet driver, which I was able to do in the end.  However, that did not solve my internet problems.  Still, web pages will random be unable to load, and my connection cuts in and out.  Any ideas as to what may be causing this?  Thanks.Not many ideas. This is a pretty common shortcoming of the driver tg3. I do notice the README includes:> Driver Build Options
====================

This version of the tg3 driver contains support for Energy Efficient Ethernet.
The feature is on by default but can be disabled at compile time by adding
"TG3_EXTRA_DEFS=TG3_NO_EEE" to the make command line.I wonder if some kind of power saving mechanism is trying incorrectly to reduce power to the device. I suggest you recompile as follows:```
cd Desktop/tg3-3.124c
make clean
make TG3_EXTRA_DEFS=TG3_NO_EEE
sudo make install
```Note any errors or warnings. Then tell us if it is better or the same.

I notice this is a driver parameter:> $ modinfo tg3
filename:       /lib/modules/3.5.0-18-generic/updates/tg3.ko
firmware:       tigon/tg3_tso5.bin
firmware:       tigon/tg3_tso.bin
firmware:       tigon/tg3.bin
version:        3.124c
license:        GPL
description:    Broadcom Tigon3 ethernet driver
author:         David S. Miller (davem@redhat.com) and Jeff Garzik (jgarzik@pobox.com)
srcversion:     D01ED9A7BF2C3956E212A63
<snip>
depends:        
vermagic:       3.5.0-18-generic SMP mod_unload modversions 686 
parm:           tg3_debug:Tigon3 bitmapped debugging message enable value (int)
[COLOR="Red"]parm:           tg3_disable_eee:Disable Energy Efficient Ethernet (EEE) support (int)[/COLOR]
We may have to experiment a bit more, but my assumption, based on the README, is that now the default is *disable* eee.

---

### Post by 1cube1wheel on 2012-11-30
Thanks for the info.  I recompiled without EEE and will see how it performs throughout the day.  I'll keep you posted.

---

### Post by 1cube1wheel on 2012-11-30
Unfortunately, that does not seem to have fixed anything.  The same problems are still occurring.

---

### Post by 1cube1wheel on 2012-11-30
If it's a problem with the driver, and no other solutions work, could I potentially fix this by buying a new NIC?

---

### Post by chili555 on 2012-11-30
> **1cube1wheel said:**
> If it's a problem with the driver, and no other solutions work, could I potentially fix this by buying a new NIC?Oh, yes! I would certainly do a bit of research and try to get one with a trouble-free chipset.

---

### Post by 1cube1wheel on 2012-12-07
So, after some research I found an Intel NIC that works well with Linux.  I have installed it and its drivers, but I am still having the same problems.  

Could this have something to do with the drivers for my old controller still being active?  Perhaps I installed the driver incorrectly, so I will go back and do that again, but I didn't know if there are any common steps I have to take when installing a new NIC driver that I may have missed.   Thanks.

---

### Post by chili555 on 2012-12-07
If you got an Intel card, reinstalling your old driver won't help. Is your old driver even loaded?```
lsmod | grep tg3
```May we see:```
nm-tool
ping -c3 www.google.com
ping -c3 8.8.8.8
```If you've had the trouble with two ethernet cards and three drivers, don't we suspect the trouble is a wrong setting in Ntework Manager or in the router? Do other computers attached to the router have similar difficuties?

In Network manager, you should ideally have *NO* settings inserted by you. Please see attached.

---

### Post by 1cube1wheel on 2012-12-07
Oh no, I didn't mean re-installing the old driver, I meant re-installing the new Intel driver.  So, I removed the old e1000 Intel driver, re-installed the new e1000e driver, and blacklisted the tg3 driver for my old NIC.  However, I am still having the same problems. 

I have entered none of my own settings in the network manager that you posted.  Here are the three things you requested: 

```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        68:05:CA:0D:33:44

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        BC:5F:F4:5A:24:2D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```


```
ping -c3 www.google.com
PING www.google.com (173.194.75.106) 56(84) bytes of data.
64 bytes from ve-in-f106.1e100.net (173.194.75.106): icmp_req=1 ttl=46 time=25.0 ms
64 bytes from ve-in-f106.1e100.net (173.194.75.106): icmp_req=2 ttl=46 time=25.7 ms
64 bytes from ve-in-f106.1e100.net (173.194.75.106): icmp_req=3 ttl=46 time=25.6 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 25.071/25.516/25.780/0.342 ms

```


```
ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=52 time=20.9 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=52 time=16.0 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=52 time=20.0 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 16.098/19.020/20.912/2.102 ms

```

Neither of the two Windows machines that I have on this network are having any connection issues.  Let me know if the above ouput tells you anything.  Thanks for the help.

---

### Post by chili555 on 2012-12-07
> and blacklisted the tg3 driver for my old NIC. Please double-check, because it's loaded:> - Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           noAfter you tweak the blacklist, remove the loaded module:```
sudo modprobe -r tg3
```Your pings look great! They suggest no networking or driver problems. Are there any interesting clues here?```
firefox www.google.com
```See if there is an error or clue in the terminal output.

---


---
title: "Toshiba Satelite Wireless not working"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by backfour94 on 2009-07-12
Hi, my son has bought a Toshiba Satelite Lap Top and I'd like him to use Ubuntu rather than Vista.

I've loaded Ubuntu from an 8.10 live disk and it is starting Ok but the wireless card doesn't seem to be being recognised.

(from an ispci command that I found from another post, I have no idea what it means, it looks like it has an Atheros AR242x wireless card).

One question before I continue, will I be able to get the card working from the live disc, i.e. proove that it works before going for a dual boot, or will I have to go install to the hard drive?

Thanks.

---

### Post by superprash2003 on 2009-07-12
post output of the following from the terminal
1)lshw -C network
2)iwconfig

---

### Post by backfour94 on 2009-07-13
thanks, there's a lot to type in for the first command, is there a specific netwotk that you're looking for? I get:

*-netwotk
description: Ethernet interface

*-network Unclaimed
description Ethernet controller

*-netwotk DISABLED
description: Ethernet interfce


For the second command I get:
lo no wireless extensions
eth0 no wireless extensions
pan0 no ethernet extensions

---

### Post by superprash2003 on 2009-07-13
cant you just copy paste.. if that machine has no internet access , then you can copy paste to a file and post it here..

---

### Post by backfour94 on 2009-07-13
how's this?

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:c3:1b:76
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:58:62:64:c7:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ubuntu@ubuntu:~$

---

### Post by darco on 2009-07-13
Maybe you need to turn on the wireless switch thats on the laptop?
Im just guessing here ...

darco

p.s. check this [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.htm](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.htm)

---

### Post by backfour94 on 2009-07-13
It' on and the wireless works fine under Vista.

---

### Post by Shpongle on 2009-07-13
maybe try jaunty it has better support than intripid , that was the case with my friend and his card worked with jaunty, think his was a broadcom though

---

### Post by backfour94 on 2009-07-13
yea maybe I'll do that.  I had the intrepid disc that I had used on another PC, with a fixed lan connection, so thought I'd give that a go and let the autoupdate update to jaunty.  But maybe I'd just be better off downloading the latest version.

---

### Post by backfour94 on 2009-07-14
Yep that worked Jaunty did it.  thanks

---


---
title: "Please help:I fix it then I lose it after reboot"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by oth8man on 2009-03-14
Hi everyone this my first thread in the forums:popcorn: and Ubuntu is new to me:KS

I hope someone will help me with my problem, please

When I install Ubuntu:D in my laptop hp tx2000 the wireless didn't work so I found this instructions to fix it :

**********
Ndiswrapper is your best bet here. In synaptic and install ndiswrapper-common, ndiswrapper-utils-1.9, and cabextract. Those will help. Now I have tried a lot of drivers and this one gave me the best luck:
[http://h18000.www1.hp.com/support/fi...oad/24001.html](http://h18000.www1.hp.com/support/fi...oad/24001.html)

In the terminal navigate to the file you downloaded the file to and type:
Code:

sudo cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

and you will want to do a "sudo gedit /etc/modules" and add ndiswrapper to the end of it. That will make ndiswrapper open on boot.
****************

And it's works but after while I don't know way when I log in it doesn't work, and it's doesn't even show that I have wireless dives So I followed the instruction again but NOTHING
After some research I found this code and I try it and it works:o

**********
sudo modprobe -r b43 b44 b43legacy ssb ndiswrapper wl bcm43xx
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
**********
but when I reboot again I have to rewrite the same code again to make it work:(

Will that's all I know it's long story but I think it's butter to give all the details to know the cause . Thanks

---

### Post by shane8002 on 2009-03-14
My friend has that same computer and if im not mistaken it has a broadcom wireless card right?   He put ubuntu 8.04 on his and after updating it, it fetched the drivers for his card and it works great.

---

### Post by Favux on 2009-03-14
Hi oth8man,

I also have a TX2000 with Intrepid (8.10) installed.  I installed the Broadcom proprietary driver from System>Administration>Hardware Drivers.  The driver is Broadcom STA wireless driver (wl).  It didn't work right because of a problem with NM (Network Manager).  But I got it to work through NM using this work around:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I hope this is helpful.

---


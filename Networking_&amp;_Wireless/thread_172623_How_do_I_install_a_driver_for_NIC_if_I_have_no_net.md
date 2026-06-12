---
title: "How do I install a driver for NIC if I have no network to get driver :):)"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by carlos123 on 2006-05-09
I just bought a Toshiba Satellite M70-DL3 that has an Intel PRO/Wireless 2915ABG wireless card in it.  I know there is a Linux driver, I know where to get it, I even have instructions on how to install it under Linux, but how do I install it under Ubuntu if I am unable to connect to the Internet through Ubuntu but only through Windows XP?  

My laptop runs Windows XP.  I have to reboot to Windows XP to access the Internet.  My laptop has no floppy drive (that I could format in VFAT and then copy the driver to - reading it once booted into Ubuntu again).  I suppose I could buy a USB flash drive, copy the driver to it, reboot to Ubuntu, copy the driver from the flash drive (assuming Ubuntu recognizes it), and so forth.  Is there an easier way to do this?  

I am looking forward to using Ubuntu but without a working wireless card it is useless to me.  Any input would be appreciated.  

Thanks.

---

### Post by elamericano on 2006-05-09
First you install Ubuntu, and that will make space for itself on your current hard drive. Your wireless card might work already. Many people think that Linux is like Windows, and that most drivers aren't included on the CD. If you have common hardware, more than 6 months old, it's probably there.

If the wireless card is not working yet, plug in a wired ethernet connection and run the update manager. Now your card will probably be working. If it's still not detected, you can download the driver and follow the instructions.

If for some reason you don't have access to a wired connection, you can use Windows to download your file to the C:\ drive, then reboot into Linux, and you will be able to read the file from there.

Something doesn't work, just post here what you tried and how far you got.

---

### Post by carlos123 on 2006-05-09
Thanks very much elamericano (nice handle you have.  I should have called myself elgringo or something similar since I too am an americano LOL).  

Anyway thanks very much for your input.  Last night when I thought about it some more it dawned on me that I can bypass the wireless card and just hook up my laptop through the RJ45 port into an ethernet cable (which is the way our desktop is hooked to the router).  Assuming Ubuntu would work with that I could then download the needed driver and install it.  

Update manager heh?  I will have to look up docs on that to find out what it is and how it can help me.  

I will post back and report when things are working.  Ubuntu seems like a really good distribution.  I have been a Gentoo user for years but these days I just don't have the time to fiddle with stuff and fix stuff that breaks with every update like I was having to do with Gentoo.  Hopefully Ubuntu will be more of a use it out of the box type of distro with less time consuming maintenance headaches involved.  

Carlos

---

### Post by carlos123 on 2006-05-09
Just wanted to report that my networking problems went away as a result of using the Ubuntu Dapper Beta release.  I am now accessing the internet from the CD and am in the process of installing Ubuntu unto my hard disk (which has Windows XP).   I didn't have to download, unpack, or install any drivers for my NIC card as the Dapper Beta release apparently had the correct driver for it.  I just made some changes under System->Administration->Networking and away I went.  Way cool!  

Little in the way of tinkering (as I had to often do under Gentoo Linux) and so far, more in the way of actually having a working installation that I can use.  

Thanks again!

Carlos

---


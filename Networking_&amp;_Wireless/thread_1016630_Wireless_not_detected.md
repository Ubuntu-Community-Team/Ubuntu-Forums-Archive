---
title: "Wireless not detected"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by Matt B on 2008-12-20
Hi,

Over the last week or so I have been attempting to switch to Ubuntu using my laptop, which is a Vye S18 ([http://www.netbooks.uk.com/product.php/vye_s18](http://www.netbooks.uk.com/product.php/vye_s18)) and I have had a couple of problems.

The first was the fact I couldn't see the desktop! But with the help from ubuntuforums, that has now been fixed, and another problem has presented itself...

I can't seem to get my wireless working. It didn't seem to be detected out of the box, and I am unsure how to get it working.

I am unsure whether this will be of help, but I saw how-to's asking others to post the output of these commands...

> matt@mattslaptop:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:c2:e2:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.5 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:06:7c:41:d0:1b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I was under the (perhaps incorrect) impression that the wireless chipset is USB based...
> 
matt@mattslaptop:~$ sudo lsusb
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 18e8:6206 Qcom 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Does anyone have any idea how to proceed? I have installed the GUI version of ndiswrapper from Synaptic, but I don't have a .inf driver for the wireless card, as the drivers are available at [www.vyepc.com](www.vyepc.com) but it is a '[setup.exe]("http://www.vyepc.com/?sec=3&page=6")' which automatically installs the drivers on windows for you.

As an aside, it appears Vye have 'unsupported' Linux driver available on their website:

[http://www.vyepc.com/?sec=3&page=6]("http://www.vyepc.com/?sec=3&page=6")

How would I go about installing this?

I am now at a bit of a loss... Any other help would be really appreciated!

Matt

---

### Post by ieee488 on 2008-12-20
Go to a Windows PC, and run the setup.exe and and see if it will extract to a directory. Even if it "installs" the drivers it won't do any harm. Take the INF file from the directory over to your laptop.


Download those tar files.
Winzip should be able to uncompress them.
Inside there may be some text files that explains how to use them.

Good luck.

---

### Post by Matt B on 2008-12-20
Unfortunately it isn't that kind of executable - if I try and run it, it just runs and then rolls back when it realises you don't have the device. However, I have re-done everything so I now have a dual-boot setup on the machine - maybe somehow I can find out where the INF file is located on the Windows partition? I will give it a go.

The tarball from Vye doesnt have a readme - can someone please talk me through how to install it? I am presuming using the Linux drivers will in theory be better than using ndiswrapper?

---

### Post by ieee488 on 2008-12-20
In all likelihood with the *.tar files, you will to build the driver by running the **make** file.

Some purists may object to using ndiswrapper. And there may be some features that don't work. However, there is also no guarantee that the Linux drivers will support all the features either.

---

### Post by iponeverything on 2008-12-20
[http://www.vyepc.com/vyesupport/S18/Drivers/Linux%20unsupported/w89c35-wpa37_Linux26.tar.tar](http://www.vyepc.com/vyesupport/S18/Drivers/Linux%20unsupported/w89c35-wpa37_Linux26.tar.tar)

Just looked at this. Nothing to compile just a binary module compiled for fedora core 4. 

ref: 
[http://angel-de-vicente.blogspot.com/2007/04/details-about-setting-up-wifi.html](http://angel-de-vicente.blogspot.com/2007/04/details-about-setting-up-wifi.html)

I would try windows driver under using ndiswrapper, the inf should be:

wbsecdrv.inf

---


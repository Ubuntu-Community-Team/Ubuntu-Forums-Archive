---
title: "Broadcom BCM4323"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2013-01-20
I am trying to install this USB Wireless adaptor on a Compaq 64 bit system running Ubuntu 12.10.

I think I need bcmwlhigh6.inf.

Using ndisgtk I intalled bcmwlhigh5.inf (I think this is the 32bit  driver) but it didn't work.

I have the Windows install CD but (using WINE for the first time) I can't find the file.

Any help or advice would be welcome

---

### Post by mörgæs on 2013-01-20
Did you read the sticky thread in this section?

---

### Post by bill-lancaster on 2013-01-21
Thanks, have now read the sticky threads and still am stuck.

When I run the Windows Wireless Driver I get:-

Module could not be loaded. Error was:

FATAL: Module ndiswrapper not found.

Is the ndiswrapper module installed?

So:-

~$ sudo apt-get install ndiswrapper-dkms
[sudo] password for bill:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 242 not upgraded.

~$  sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

$ ndiswrapper -l
bcmwlhigh5 : invalid driver!

So, bcmwlhigh5 is invalid.  Perhaps bcmwlhigh6 would work but cannot find bcmwlhigh5.inf

I'm not far from abandoning this wireles usb for something that works!

---

### Post by bkratz on 2013-01-21
> **bill-lancaster said:**
> Thanks, have now read the sticky threads and still am stuck.

When I run the Windows Wireless Driver I get:-

Module could not be loaded. Error was:

FATAL: Module ndiswrapper not found.

Is the ndiswrapper module installed?

So:-

~$ sudo apt-get install ndiswrapper-dkms
[sudo] password for bill:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 242 not upgraded.

~$  sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

$ ndiswrapper -l
bcmwlhigh5 : invalid driver!

So, bcmwlhigh5 is invalid.  Perhaps bcmwlhigh6 would work but cannot find bcmwlhigh5.inf

I'm not far from abandoning this wireles usb for something that works!




I did find the 64bit xp files though this link.  Don't have the device so did not go further.

[http://www.backtrack-linux.org/forums/showthread.php?t=54451](http://www.backtrack-linux.org/forums/showthread.php?t=54451)

---

### Post by bill-lancaster on 2013-01-21
I have seen some postings that sugest that ndiswrapper won't work on a 64 bit (Intel) system - I wonder if this is my problem.

---

### Post by bkratz on 2013-01-21
> **bill-lancaster said:**
> I have seen some postings that sugest that ndiswrapper won't work on a 64 bit (Intel) system - I wonder if this is my problem.




See post 2 in this thread

[http://ubuntuforums.org/showthread.php?t=2104162](http://ubuntuforums.org/showthread.php?t=2104162)

---

### Post by bill-lancaster on 2013-01-21
Thanks for the link, the author seemed to end up with bcmwlhigh5.inf anyway.

So I thought I'd follow his steps:-

:~$  ndiswrapper -a 0846:9011 bcmwlhigh5
gave:-
Driver 'bcmwlhigh5' is already used for '0846:9011'

and Wireless Networks Drivers shows:- bcmwlhigh5 hardware present:yes

This seems like a step forward but I still don't have a working wireless connection

---

### Post by bkratz on 2013-01-21
> **bill-lancaster said:**
> Thanks for the link, the author seemed to end up with bcmwlhigh5.inf anyway.

So I thought I'd follow his steps:-

:~$  ndiswrapper -a 0846:9011 bcmwlhigh5
gave:-
Driver 'bcmwlhigh5' is already used for '0846:9011'

and Wireless Networks Drivers shows:- bcmwlhigh5 hardware present:yes

This seems like a step forward but I still don't have a working wireless connection


Please post the outputs of:


```
ifconfig
sudo iwlist scan
lshw -C Network
```

using the code tags for clarity

---

### Post by bill-lancaster on 2013-01-21
Thank you very much for your interest: Here are the results (sorry - don't know what is meabt by 'code tags')

ifconfig

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 4c:72:b9:95:63:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1984 (1.9 KB)  TX bytes:1984 (1.9 KB)

~$ sudo iwlist scan

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

~$ lshw -C Network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: 4c:72:b9:95:63:bb
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 multicast=yes port=twisted pair
       resources: irq:44 memory:f7c00000-f7c3ffff ioport:e000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by bkratz on 2013-01-21
Code tags are used for readability,  the box around the requested inputs was created like the following

[http://i.stack.imgur.com/zADbK.png](http://i.stack.imgur.com/zADbK.png)

I don't even see anything related to networking, just ethernet in your listings, you might post the output of 

lsusb

that is LSUSB in lowercase.

---

### Post by bill-lancaster on 2013-01-21
Thanks again,
~$ lsusb
gave these results:-

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 004: ID 0461:0010 Primax Electronics, Ltd HP Keyboard
Bus 002 Device 003: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 007: ID 0781:556b SanDisk Corp.

---

### Post by bkratz on 2013-01-21
Page 14 of this thread is probably worth reading, esp if you are still having problems with ndiswrapper

[http://ubuntuforums.org/showthread.php?t=1964173&page=14&highlight=0846%3A9011](http://ubuntuforums.org/showthread.php?t=1964173&page=14&highlight=0846%3A9011)


Here is another thread

[http://ubuntuforums.org/showthread.php?t=2106615](http://ubuntuforums.org/showthread.php?t=2106615)


Found another

[http://ubuntuforums.org/showthread.php?t=2102847](http://ubuntuforums.org/showthread.php?t=2102847)

---

### Post by bill-lancaster on 2013-01-22
Thank you bkratz, have studied those links you sent and believe I've already been down those roads.

Just to give a bit info about my situation.

I have a new Compaq 64 bit machine running 12.10 64 bit.  I over-wrote the entire hd when installing Ubuntu.

I also have a spare HD with win 8 & Ubuntu installed.

When the Broadcom usb was installed under win 8 it took just seconds and worked very well.

---

### Post by bill-lancaster on 2013-01-23
Thank you all for your support & help on this but I've given in and purchased an AirLink 101 USB adaptor - it took about 20 seconds!

---

### Post by bkratz on 2013-01-23
> **bill-lancaster said:**
> Thank you all for your support & help on this but I've given in and purchased an AirLink 101 USB adaptor - it took about 20 seconds!




Just checked in and noticed your post----at least you got something working, sorry we didn't have more luck with the other one.

---


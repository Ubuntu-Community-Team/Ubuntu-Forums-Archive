---
title: "My Franklin CGU-628A modem do not have Linux OS Installer"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by theonlydel on 2010-01-13
Hi all my dear frens, I am using Ubuntu 9.10. I just bought a franklin CGU-628A wireless mobile broadband modem. However the modem didn't have the linux OS installer as mention in Franklin Official Website >>> [http://http://www.franklinwireless.com/?doc=bbs/gnuboard.php&bo_table=product&wr_id=14]("http://http://www.franklinwireless.com/?doc=bbs/gnuboard.php&bo_table=product&wr_id=14")

Thus, I need some help if there is anyone that use this type of modem to share me the copy of linux OS installation package.....pls...ur help would be really appreciate....tq

---

### Post by chili555 on 2010-01-13
From their FAQ:> Linux

Q . Do we support Linux?

A . Yes, we support Ubuntu Version of Linux. As of now we support up to 7.1. However, we are testing version 7.2. Since we are now at Ubuntu version 9.10, that is, 2 1/2 years later, I sort of doubt that the installer they provide would do us much good. Let's ask the device for its chipset details and try to get it going. Please insert the device and open a terminal and do:```
lsusb
```Please post the result. Thanks.

---

### Post by changingstate on 2010-01-13
Spotted this on the Puppy linux site, taken from usb_modeswitch :

C-motech CGU-628 (aka "Franklin Wireless CGU-628A" aka "4G Systems XS Stick W12")

---

### Post by theonlydel on 2010-01-13
this what it shows...

```
theonlydel@theonlydel-aspire:~$ lsusb
Bus 003 Device 002: ID 0489:e011 Foxconn / Hon Hai 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b160 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 16d8:6281 CMOTECH Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
theonlydel@theonlydel-aspire:~$ 
```

trying to find it also in other forums, yet still no solution...

---

### Post by changingstate on 2010-01-13
Could you please unplug the modem, then run the command below :

```
sudo apt-get install usb-modeswitch
```Then plug the device back in and run lsusb again, please?

---

### Post by theonlydel on 2010-01-13
same code showed

```
theonlydel@theonlydel-aspire:~$ sudo apt-get install usb-modeswitch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gcom wvdial
The following NEW packages will be installed:
  usb-modeswitch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 http://my.archive.ubuntu.com karmic/universe usb-modeswitch 1.0.2-1 [29.7kB]
Fetched 29.7kB in 1s (18.9kB/s)                        
Selecting previously deselected package usb-modeswitch.
(Reading database ... 157578 files and directories currently installed.)
Unpacking usb-modeswitch (from .../usb-modeswitch_1.0.2-1_i386.deb) ...
Processing triggers for man-db ...
Setting up usb-modeswitch (1.0.2-1) ...
theonlydel@theonlydel-aspire:~$ lsusb
Bus 003 Device 002: ID 0489:e011 Foxconn / Hon Hai 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b160 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 16d8:6281 CMOTECH Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
theonlydel@theonlydel-aspire:~$ lsusb
Bus 003 Device 002: ID 0489:e011 Foxconn / Hon Hai 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b160 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 16d8:6281 CMOTECH Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
theonlydel@theonlydel-aspire:~$ 
```

---

### Post by changingstate on 2010-01-13
**Okay, read this entire post before doing anything**

I've done some reading up on the usb_modeswitch package. This command should allow us to test being able to get your modem working :

```
sudo /usr/sbin/usb_modeswitch --default-vendor 0x16d8 --default-product 0x6281 --message-content 55534243d85dd88524000000800008ff524445564348470000000000000000
```Running lsusb after, I'd expect to see a change to the CMOTECH device.

I'm only 99% sure this command is safe. You may prefer to NOT do this and wait for other opinions. Which is fine.

---

### Post by theonlydel on 2010-01-26
this what happen and the code was

```
theonlydel@theonlydel-aspire:~$ sudo /usr/sbin/usb_modeswitch --default-vendor 0x16d8 --default-product 0x6281 --message-content 55534243d85dd88524000000800008ff524445564348470000000000000000
[sudo] password for theonlydel: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 Found default devices (1)
Accessing device 002 on bus 004 ...
Using endpoints 0x09 (out) and 0x88 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

Received inquiry data (detailed identification)
-------------------------
  Vendor String: CMOTECH 
 Product String: Mass Storage    
Revision String: 2.31
-------------------------

Device description data (identification)
-------------------------
Manufacturer: CMOTECH CO., LTD.
     Product: USB Mass Storage
  Serial No.: 000000000002
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x09 ...
 OK, message successfully sent
Device is gone, skipping further steps ...
-> Run lsusb to note any changes. Bye.

theonlydel@theonlydel-aspire:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b160 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 16d8:6281 CMOTECH Co., Ltd. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1b1a:0000  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0489:e011 Foxconn / Hon Hai 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
theonlydel@theonlydel-aspire:~$ 
```

i think the cmotech not changing right??

---

### Post by mmeandro on 2010-04-11
did you get this going
i have this modem
what package do i need to talk to it in linux?

---

### Post by pdc on 2010-04-12
If you read this post here

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=259&sid=6b1837ebdeb9cce1145c73f6ec7b56ed](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=259&sid=6b1837ebdeb9cce1145c73f6ec7b56ed)

the first post talks of getting a Franklin CGU-628A working using usb_modeswitch;

the latest version is 1.1.1 and it seems to autoconfigure all by itself;

if you firstly plug your modem in and tell us what 

> lsusb gives you 

this is the link for the usb_modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

and here is where you download the debian version from (it is a .deb package)

[http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)

---


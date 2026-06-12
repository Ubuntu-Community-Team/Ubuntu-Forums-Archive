---
title: "Mobile Modem ACM-001 Cannot Detected by Karmic"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by nugroho.redbuff on 2010-10-28
dear ubuntu Users and developers.
At Saturday, 23rd October 2010 I bought a USB CDMA Modem named AX manufactured by Alltronix and has series 
labeled ACM-001. The chipset is Qualcom. It didn't work on My Karmic Koala nor Lucid Lynx.

I try to check some condition by writing some command in shell prompt like: tail -f /var/log/messages, lsusb,
and modprobe. Here is the results.

result of tail -f /var/log/messages
Oct 24 01:37:54 ubuntu kernel: [  500.464348] usb 2-2: new full speed USB device using uhci_hcd and address 3
Oct 24 01:37:55 ubuntu kernel: [  500.628220] usb 2-2: configuration #1 chosen from 1 choice
**Oct 24 01:37:55 ubuntu kernel: [  500.636305] scsi5 : SCSI emulation for USB Mass Storage devices.**

results of lsusb:
root@ubuntu:~# lsusb
Bus 005 Device 002: ID 0a5c:2162 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 05c6:1000 Qualcomm, Inc.**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:0156 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 0951:1625 Kingston Technology 
Bus 001 Device 002: ID 0ac8:3420 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

result of modprobe:
root@ubuntu:~# modprobe vendor=0x05c6 product=1000
**FATAL: Module vendor=0x05c6 not found.**

I use netbook named BYON Chameleon N 610 GA. Intel Atom inside, 1028 MB RAM, Intel Chipset, and 160 GB SATA HDD.

Please help me to use this modem then I can online with. Just mail me at [EMAIL="nugroho.redbuff@gmail.com"]nugroho.redbuff@gmail.com[/EMAIL].
Thanks for your helps.:(

---

### Post by pdc on 2010-10-28
looks like you need usb_modeswitch, to switch the way this device is seen;

after switching, it will be seen as a modem; now, it is seen as a storage-device;

go here

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

it tells you how to download: you need the programme and the data file;

the debian repository link should let you download the right version for  your computer: ie i586 or whatever; as a .deb package

that you install by letting gdebi package installer do the work; 

the data is a tar.bz2 file; 


by the way, after switching its ID in lsusb should be

> 0af0:6600

---

### Post by nugroho.redbuff on 2010-10-29
I have try to execute usb_modeswitch. I use usbsnoop too ([www.pcausa.com/Utilities/UsbSnoop/](www.pcausa.com/Utilities/UsbSnoop/)). Then I make a new confuguration named 05c6:100:uMa=Qualcomm. The content just like below:
> 
DefaultVendor= 0x05c6
DefaultProduct=0x1000

TargetVendor=  0x0af0
TargetProduct= 0x6000

CheckSuccess=10

//MessageContent="55534243123456780000000000000601000000000000000000000000000000"
MessageEndpoint = 0x05
MessageContent = "55534243d878c1820010000080000a2800000003c700000200000000000000"
NeedResponse=1



and here is the executing syntax:
> 
usb_modeswitch  -c /etc/usb_modeswitch.d/05c6:1000:uMa=Qualcomm


and here is the result:
> 
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 002 on bus 003 ...
Using endpoints 0x05 (out) and 0x85 (in)
Using endpoints 0x05 (out) and 0x85 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: OEM     
   Model String: Storage         
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: Qualcomm, Incorporated
     Product: OEM USB Storage
  Serial No.: not provided
-------------------------
Setting up communication with interface 0 ...
Using endpoint 0x05 for message sending ...
Trying to send message 1 to endpoint 0x05 ...
 OK, message successfully sent
Reading the response to the message (CSW) ...
 OK, response successfully read (0 bytes).
Resetting response endpoint 0x85
Resetting message endpoint 0x05

Checking for mode switch (max. 10 times, once per second) ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Waiting for original device to vanish ...
 Original device still present after the timeout


Any suggestion? :shock:

---

### Post by nugroho.redbuff on 2010-10-31
Today, Monday November 1st I try to execute all script which have prefix 05c6:1000:*. When I run

> usb_modeswitch -c /etc/05c6:1000:uMa=AnyDATAthen I do lsusb,

here is what i get:

**Bus 002 Device 005: ID 05c6:6000 Qualcomm, Inc.** <-- the product ID is changed.

Now i can go on line with my new modem.

---

### Post by 0odevilzo0 on 2010-11-28
hello mr nugroho.redbuff.
can you explain more clearly the step for installing this modem on linux?
i bought it too, and wanna try to use it on linux...
thanx for your help...
---------------------------------------------
mas tolong bantuin ya cara install driver nya di linux, saya kpingin pakai dilinux jg, sebelum nya saya pake VMWARE utk konekin modem nya ke internet... cape...
nah kalo dgn cara mas ini bisa kan saya ga perlu lagi pake dual OS linux dan Windows dengan bantuan VMWARE... makasih ya mas atas kemurahan hati nya...   :)

---


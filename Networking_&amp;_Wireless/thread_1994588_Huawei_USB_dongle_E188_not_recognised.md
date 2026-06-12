---
title: "Huawei USB dongle E188 not recognised"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2012-06-03
HI, 

Having problems that you may be able to help me out with.  Have been working at if for about 12 hours with no resolution.

I have a USB dongle (Huawei E188 ) that works perfectly with windows but is not recognised in Ubuntu 12.04 Pangolin. When I try to use the Ubuntu Network Manager, the Dongle is not recognised as being an internet device.

Some times, on plugin, it is recognised as a CD-Rom  Other times, not much happens.

However, it works perfectly on Windows (where I'm sending this through.) but I prefer Linux

usb-modeswitch installed with errors/not present after an internet search.  Gave up on it. 

I'll change systems to get a few screen grabs and post them here.

Can anybody provide some simple advice on how to get the Dongle recognised please.

Thanks in advance,

Andrew F

---

### Post by Andrew F in Australia on 2012-06-03
As always, the answer pops up immediately after you post for advice.

edit the etc/modules file and tell Ubuntu that it's a modem

```

Bring up a terminal window  <ctrl>+<alt> + t 

sudo gedit /etc/modules
append the following line to your exceptions.

[B]usbserial vendor=0x12d1 product=0x1c07

[/B]save and exit

reboot (either by typing this word in the terminal window or the usual way)

```found the solution on this website - Huawei wireless dongle working happily with Ubuntu now.

[http://forums.whirlpool.net.au/archive/1915915](http://forums.whirlpool.net.au/archive/1915915)

How do you find the product code and usbserial vendor for your USB wireless broadband dongle?

```

Bring up a terminal window <ctrl> + <alt> + t

type in lsusb

horace@horace-HP-ProBook-4730s:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 004: ID 12d1:1c07 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 1bcf:2888 Sunplus Innovation Technology Inc. 


```Look at the line with Huawei Technologies Co note the 12d1:1c07 part

The vendor code is 0x12d1 , the usbserial code is 0x1c07

The Debian wiki was very helpful here:
[http://wiki.debian.org/Huawei/E220](http://wiki.debian.org/Huawei/E220)

Thanks again,

AF

---


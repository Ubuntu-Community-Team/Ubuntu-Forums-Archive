---
title: "Problem installing a NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by newbneedhelp on 2012-01-19
I am absolutly new to the world of Linux.  I have a NetGear WNA3100 wireless usb dongle but I have trouble installing it on Ubuntu 11.10 64-bit.  Here are a list of commands and outputs.

I have used some of the other threads but it all ends up like this.

heinz@ubuntu:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/3.0.0-12-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.56
vermagic:       3.0.0-12-generic SMP mod_unload modversions 


heinz@ubuntu:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 002: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 005 Device 002: ID 0458:3019 KYE Systems Corp. (Mouse Systems) 10-Button USB Joystick with Vibration



heinz@ubuntu:~$ sudo ndiswrapper -i /home/heinz/Downloads/bcmwlhigh6/bcmwlhigh6.inf
installing bcmwlhigh6 ...


heinz@ubuntu:~$ sudo ndiswrapper -l
bcmwlhigh6 : driver installed
    device (0846:9020) present


heinz@ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by newbneedhelp on 2012-01-22
[FONT=Times New Roman][SIZE=3][COLOR=Blue]OK, I solved my own problem after reading the following blog:
[/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=3][http://blog.ferhatelmas.com/](http://blog.ferhatelmas.com/)

The issue was that ndiswrapper is not supported in 11.10 64bit so I downgraded to 10.04 L[/SIZE][/FONT][FONT=Times New Roman][COLOR=Black][SIZE=3]TS 32Bit.

I then followed one of the many step by steps and there it was working fine.[/SIZE]
[/COLOR][/FONT]

---


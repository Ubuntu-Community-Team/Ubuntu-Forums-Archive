---
title: "e1752 on ubuntu 8.04"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by blmain on 2012-05-08
Hi

I try to use the 3G dungle E1752 with Ubuntu 8.04.4

it look to be well dected on USB
elisabeth@MEKONGO:~$ lsusb
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 003: ID 07d1:3303 D-Link System
Bus 001 Device 002: ID 12d1:1446 Huawei Technologies Co., Ltd.
Bus 001 Device 001: ID 0000:0000 

I culd install USB_modeswitch
It look to well work and detect the dungle
elisabeth@MEKONGO:~$ sudo usb_modeswitch
[sudo] password for elisabeth:

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices
 Found default devices (1)
Prepare switching, accessing latest device
Looking for active default driver to detach it
 OK, driver found ("usb-storage")
 OK, Driver "usb-storage" successfully detached
Setting up communication with device
Trying to send the message
 OK, message successfully sent.
-> See /proc/bus/usb/devices (or call lsusb) for changes. Bye

I install several version of HSO driver
elisabeth@MEKONGO:~/Drivers$ ls
hso-1.14.tar.gz
hso-1.9.tar.gz
hso_26-v1.14
hso_26-v1.9
hsoconnect-py2.4_1.1.83_all.debelisabeth@MEKONGO:~/Drivers/hso_26-v1.9$ sudo ./connect.sh up
connecting
./connect.sh: 87: cannot open /dev/ttyHS0: No such file
 n inet
connected
 
add route
set nameserver

hsolink_1.0.118-1_i386.deb
icon225.tgz

As you may know icon225 include hso v16

when I do a connect.sh up it failed
elisabeth@MEKONGO:~/Drivers/hso_26-v1.9$ sudo ./connect.sh up
connecting
./connect.sh: 87: cannot open /dev/ttyHS0: No such file
 n inetelisabeth@MEKONGO:~/Drivers/hso_26-v1.9$ sudo ./connect.sh up
connecting
./connect.sh: 87: cannot open /dev/ttyHS0: No such file
 n inet
connected
 
add route
set nameserver

connected
 
add route
set nameserver
elisabeth@MEKONGO:~/Drivers/hso_26-v1.9$ sudo ./connect.sh up
connecting
./connect.sh: 87: cannot open /dev/ttyHS0: No such file
 n inet
connected
 
add route
set nameserver
elisabeth@MEKONGO:~/Drivers/hso_26-v1.9$ sudo ./connect.sh up
connecting
./connect.sh: 87: cannot open /dev/ttyHS0: No such file
 n inet
connected
 
add route
set nameserver

No way to see why the ttyhs0 is not found

Thanks for your help

---

### Post by blmain on 2012-05-08
I forgot, the right shell command to start the ghso connection is not connect.sh but hso_connect.sh
so here is the result when I try to connect 

elisabeth@MEKONGO:~/hso_26-v1.14$ sudo ./hso_connect.sh up
Using /dev/ application port.
Initializing...
Trying orange.fr ...
Connecting...
trying
trying-
trying--
trying---
trying----
Connected
We did not get an IP address from the provider, bailing ...
./hso_connect.sh: 264: cannot create /dev/: Is a directory
elisabeth@MEKONGO:~/hso_26-v1.14$ sudo ./hso_connect.sh down
Using /dev/ application port.
Bringing interface down...
hso0: ERREUR en récupérant les signaux de l'interface: Aucun périphérique de ce type
Disconnecting...
./hso_connect.sh: 264: cannot create /dev/: Is a directory
Done.

---


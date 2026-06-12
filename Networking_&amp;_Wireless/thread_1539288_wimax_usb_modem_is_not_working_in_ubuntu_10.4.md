---
title: "wimax usb modem is not working in ubuntu 10.4"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by sohoj on 2010-07-26
Im from Bangladesh using usb wimax modem for qubee.its web address is qubee.com.bd

in terninal after giving the lsusb command i get the following output 



sanjoy@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 064e:a133 Suyin Corp. 
Bus 002 Device 003: ID 1076:7f40 GCT Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sanjoy@ubuntu:~$ 

 i thin its GCT semiconductor inc


after that I give dmesg>output.text so a text file I goet which is attached.
[ATTACH]164575[/ATTACH]

pls help me.I need it badly. 

All this I done on guide of my one friend.Now I need help

---

### Post by pdc on 2010-07-27
I think you need usb_modeswitch installed

Get it from here

[http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

scroll down the page to the section that is about usb_modeswitch

download what is right for you:

ie if using 32bit Ubuntu, download the i386;

your system should offer to install; use gdebi installer;

this latest version of usb_modeswitch (1.1.3-1) should configure by itself;

if you do 

> lsusb

**after installing usb_modeswitch**, and rebooting, your device should have the **new ID** of

> 1076:7f00

if so, 

then RIGHT-CLICK on network manager: left-most of the icons at top right;

and configure

---

### Post by sohoj on 2010-07-27
AT first thanks a lot for the reply.

I tried as per ur advise. Firstly I download the mod switch for 32 bit from other PC in .deb format then installed.After that I restart the pc then check with lsusb command in terminal but my device dont get the new id its showing the same id .SO I dont found anything on the network manager.

Pls say now what can I do


My modem manufacturer link with modem picture--[http://www.seowonintech.co.kr/en/product/detail.asp?num=111&big_kind=B04&middle_kind=://]("http://www.seowonintech.co.kr/en/product/detail.asp?num=111&big_kind=B04&middle_kind=://")

---

### Post by pdc on 2010-07-27
Good news is your device is known about; and written about; on the usb_modeswitch forum;

and I believe it will switch your device and get it working for you; the posting from last Nov was guys from the Ukraine using a device just like yours; 

problem; the needed switching of the device seems a little unsteady;

I recommend you join the usb_modeswitch forum; 

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

Josh oversees the programme; and oversees the forum; what better care could you want?

He can give you tests to run etc;

I will watch the forum to see how you get along

---

### Post by sohoj on 2010-07-28
Thanks for the guide but I cant join on that forum as I dont find Authorization Code.

---

### Post by sarim on 2010-07-28
```
usb_modeswitch -v 1076 -p 7f40
```
run this in terminal to manually switch your modem.

---

### Post by sohoj on 2010-07-28
@Sarim 

after giving ur command in terminal i get the following msg


sanjoy@ubuntu:~$ usb_modeswitch -v 1076 -p 7f40

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 000 on bus 001 ...
Using endpoints 0x04 (out) and 0x83 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -1). Skipping device inquiry
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

sanjoy@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1076:7f40 GCT Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sanjoy@ubuntu:~$

---

### Post by sarim on 2010-07-28
add a sudo before command.
try this, for GCT mode.
```
sudo usb_modeswitch -v 1076 -p 7f40 -G
```

---

### Post by sohoj on 2010-07-28
sanjoy@ubuntu:~$ sudo usb_modeswitch -v 1076 -p 7f40-G

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 009 on bus 001 ...
Using endpoints 0x04 (out) and 0x83 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -2). Skipping device inquiry

USB description data (for identification)
-------------------------
Manufacturer: GCT Semiconductor, Inc.
     Product: M-WiMAX Network Adaptor
  Serial No.: 72050103
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

sanjoy@ubuntu:~$ sudo usb_modeswitch -v 1076 -p 7f40 -G

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 009 on bus 001 ...
Using endpoints 0x04 (out) and 0x83 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -2). Skipping device inquiry

USB description data (for identification)
-------------------------
Manufacturer: GCT Semiconductor, Inc.
     Product: M-WiMAX Network Adaptor
  Serial No.: 72050103
-------------------------
Warning: no switching method given.
Looking for active driver ...
 No driver found. Either detached before or never attached
 Could not claim interface (error -2). Skipping GCT sequence 
-> Run lsusb to note any changes. Bye.

sanjoy@ubuntu:~$

---

### Post by sohoj on 2010-07-28
after giving the following command i got the below output now what to do

sanjoy@ubuntu:~$ sudo usb_modeswitch -I -v 0x1076 -p 0x7f40 -G -I -i 1

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 012 on bus 001 ...

USB description data (for identification)
-------------------------
Manufacturer: GCT Semiconductor, Inc.
     Product: M-WiMAX Network Adaptor
  Serial No.: 72050103
-------------------------
Warning: no switching method given.
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Sending GCT control message 1 ...
Sending GCT control message 2 ...
 OK, GCT control messages sent
-> Run lsusb to note any changes. Bye.

sanjoy@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 1076:7f00 GCT Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sanjoy@ubuntu:~$

---

### Post by pdc on 2010-07-28
well done; you have "flipped" your device, and it is now seen as a modem;

so you need to configure it;

TRY:

LEFT-CLICK on network manager; most left of the right-hand icons on the top bar;

by any chance, do you see the network you want to connect to, shown in the list?

If not, RIGHT-CLICK on network manager;

click on mobile broadband; click ADD; select country and network as the system asks you; when setup;

then LEFT-CLICK on network manager to see if what you set up is there .

---

### Post by sohoj on 2010-07-28
first of all its wimax modem so is it called mobile broadband? Im not sure.I dont find anything on network manager

---

### Post by sarim on 2010-07-29
plz give a try with wvdial. install wvdial, then run,
```
sudo wvdialconf
```

---

### Post by sohoj on 2010-07-30
insttalled wvdial but it said no modem is found

---

### Post by pdc on 2010-07-30
please tell us (with your device plugged in) what 

> lsusb

and please **copy and paste** this command into a terminal

> dmesg | grep tty

and copy and paste the results back here please

---

### Post by sohoj on 2010-07-31
sanjoy@ubuntu:~$ sudo usb_modeswitch -I -v 0x1076 -p 0x7f40 -G -I -i 1

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 005 on bus 002 ...

USB description data (for identification)
-------------------------
Manufacturer: GCT Semiconductor, Inc.
     Product: M-WiMAX Network Adaptor
  Serial No.: 72050103
-------------------------
Warning: no switching method given.
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Sending GCT control message 1 ...
Sending GCT control message 2 ...
 OK, GCT control messages sent
-> Run lsusb to note any changes. Bye.

sanjoy@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 1076:7f00 GCT Semiconductor, Inc.
Bus 002 Device 004: ID 064e:a133 Suyin Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sanjoy@ubuntu:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
sanjoy@ubuntu:~$

---

### Post by sarim on 2010-08-01
your modem is not detected as modem as i see in dmesg.
try this (after switching modem)

```
sudo modprobe usbserial vendor=0x1076 product=0x7f00
```

after that, try wvdialconf

---

### Post by sohoj on 2010-08-03
sanjoy@ubuntu:~$ sudo usb_modeswitch -I -v 0x1076 -p 0x7f40 -G -I -i 1
[sudo] password for sanjoy: 

Looking for default devices ...
 Found devices in default mode or class (1)
Accessing device 003 on bus 001 ...

USB description data (for identification)
-------------------------
Manufacturer: GCT Semiconductor, Inc.
     Product: M-WiMAX Network Adaptor
  Serial No.: 72050103
-------------------------
Warning: no switching method given.
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Sending GCT control message 1 ...
Sending GCT control message 2 ...
 OK, GCT control messages sent
-> Run lsusb to note any changes. Bye.

sanjoy@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a133 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1076:7f00 GCT Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sanjoy@ubuntu:~$ sudo modprobe usbserial vendor=0x1076 product=0x7f00

sanjoy@ubuntu:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
sanjoy@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
sanjoy@ubuntu:~$

---

### Post by 1R3N1CU5 on 2010-11-08
I'm from BD bro...and the new usb wimax modem released by qubee is not supported in linux! 

It comes with its own driver that automatically activates the modem on Windows...& unless the driver is installed the modem does not power on when plugged in.

I did speak to a qubee technical person, & he told me that mac & windows are currently supported...& that he's urging his boss to create another driver for Linux users :-k

Who knows how long it will take to be released, if it ever does! :(

---

### Post by H-Racky on 2011-03-08
> **1R3N1CU5 said:**
> I'm from BD bro...and the new usb wimax modem released by qubee is not supported in linux! 

It comes with its own driver that automatically activates the modem on Windows...& unless the driver is installed the modem does not power on when plugged in.

I did speak to a qubee technical person, & he told me that mac & windows are currently supported...& that he's urging his boss to create another driver for Linux users :-k

Who knows how long it will take to be released, if it ever does! :(

Do you know if the driver was released? [The manufacturer]("http://www.seowonintech.co.kr/en/product/detail.asp?num=111&big_kind=B04&middle_kind=") says the modem is supported by Linux, but they don't say which distro and I can't manage to have it working under ubuntu 10.10

---

### Post by Ersul on 2011-05-31
One guy from Ukraine has written driver for this modem. Check it out: [http://code.google.com/p/gctwimax/downloads/list](http://code.google.com/p/gctwimax/downloads/list)

Download latest version, install it then try:
$ sudo ./wimax --login=XXXXXX --pass=YYYYYY
$ sudo dhclien wimaxX

---


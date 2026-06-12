---
title: "Alltel USB EVDO"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by cssutto on 2009-06-04
Alltel
Huawei 168 
Ubuntu 8.04

Thinkpad T60p



This air card works fine in Windows but I can not get Ubuntu to find it.

Help would be appreciated.

CSSJR

---

### Post by GeorgeVita on 2009-06-05
Hi **cssutto**,

please boot without the modem, wait for the system to stabilise, attach the modem, wait 20 seconds, open a terminal window (Applications, Accesories, Terminal) and try:

[B]dmesg
lsusb
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*[/B]

(each line is a different command, press <enter> after typing it)

Post here the last 10-15 lines of **dmesg** (concerning /dev/ttyUSBx and usbserial) and also the output of the other two commands.

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/tty...** will list any configured serial communication ports.

Also take a look at my HowTo for a similar modem:
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)

Regards,
George

---

### Post by cssutto on 2009-06-05
Thank you.

I am posting this on a windoze machine.  

It will be tonight before I can follow your instructions.

Thanks for the help.

CSSJR

---

### Post by cssutto on 2009-06-06
George:

Here are the results:

[ 1416.587478] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[ 1416.598416] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1426.636163] eth0: no IPv6 routers present
[ 1512.559773] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 1512.719656] usb 1-2: configuration #1 chosen from 1 choice
[ 1512.728850] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1512.729266] usb-storage: device found at 4
[ 1512.729271] usb-storage: waiting for device to settle before scanning
[ 1517.717680] usb-storage: device scan complete
[ 1517.720943] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 0
[ 1517.759812] sr1: scsi-1 drive
[ 1517.759897] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 1517.759962] sr 7:0:0:0: Attached scsi generic sg3 type 5
[ 1521.301792] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1521.307781] ISOFS: changing to secondary root



Bus 005 Device 007: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 005 Device 006: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 005: ID 03f0:2b11 Hewlett-Packard 
Bus 005 Device 002: ID 050d:0416 Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 002: ID 0a5c:2110 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 12d1:1413 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 0000:0000  


$ ls /dev/ttyu*  /dev/ttyA*  /dev/ttyH*
ls: cannot access /dev/ttyA*: No such file or directory
ls: cannot access /dev/ttyH*: No such file or directory
/dev/ttyu0  /dev/ttyu3  /dev/ttyu6  /dev/ttyu9  /dev/ttyuc  /dev/ttyuf
/dev/ttyu1  /dev/ttyu4  /dev/ttyu7  /dev/ttyua  /dev/ttyud
/dev/ttyu2  /dev/ttyu5  /dev/ttyu8  /dev/ttyub  /dev/ttyue

---

### Post by GeorgeVita on 2009-06-06
Hi **cssutto**,
from **lsusb** shown the vendorID : productID as 0x12d1 : 0x1413
and till now it is attached as scsi CDROM **sr1** (from dmesg).

EDIT: 3 ideas to test!

1. Boot with the modem attached, wait for the system to stabilise, open a terminal window and try:
**ls /dev/ttyUSB*** (USB=upper case!). If it shows /dev/ttyUSB0 1 and 2 we are OK. If not:

2. Open a terminal window:
**sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi**
search (ctrl-f) for **12d1** go below to the line that contains"...int="0x1001", edit it to "...int="**0x1413**", save and exit. Reboot and test as previous idea #1.

3. As most Huawei modems work better with 8.10 (and possibly 9.04), try an Ubuntu 8.10 liveCD, where you can also check above (#1 and #2). If you notice a "ttyUSBx" or an informative message as "mobile Broadband detected..." will be good!

I tested my E169 with 8.04 and 8.10 LiveCDs, both managed to make /dev/ttyUSB0-1-2
Huawei E169 responds as 12d1 : 1001 which included by default to the HAL definitions (your modem 0x1413 is not). 

Another way is usb_modswitch (I searched but did not found anything well described).

Regards,
George

---

### Post by cssutto on 2009-06-07
George:

Thank you.

Today is going to be very busy.  I will try your suggestions tomorrow.

For now, it is not an emergency.  I have a wireless router and it works like a charm.

My reason for the original post was that the EC168 was not compatible with the router I had.  The original PC card that worked with the old router went bad.

I ended up purchasing a new router and it works.

The need for the air card to be in the computer is for any time the router might not be usable.

Thank you for the help.

CSSJR

---


---
title: "USB cell modem not working"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by jfreak53 on 2009-06-12
Ok, I live in Guatemala and I bought a modem from my cell phone company, it is called a GBC China Bird Modem, USB.  Model # CBCPL68

Now I know for a fact that some people have gotten this modem to work in Linux, more specifically my version, 8.04.

There are directions online:  [http://luisalvarado.blogspot.com/2009/04/configurando-el-modem-tigo-gbc-en.html](http://luisalvarado.blogspot.com/2009/04/configurando-el-modem-tigo-gbc-en.html)

I did exactly what it said to do.  Running lsusb before doing anything this is what I get:
> 
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 012: ID 1c9e:1001
Bus 001 Device 003: ID 045e:0053 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000

Running dmesg before I do anything this is what I get:
> 
[13166.889845] scsi6 : SCSI emulation for USB Mass Storage devices
[13166.892101] usb-storage: device found at 12
[13166.892108] usb-storage: waiting for device to settle before scanning
[13171.890072] usb-storage: device scan complete
[13177.562450] usb 1-2: reset full speed USB device using ohci_hcd and address 12
[13177.790675] scsi 6:0:0:0: Direct-Access     USBModem Disk             1.00 PQ: 0 ANSI: 2
[13177.811629] sd 6:0:0:0: [sdb] 65536 512-byte hardware sectors (34 MB)
[13177.824642] sd 6:0:0:0: [sdb] Write Protect is on
[13177.824654] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 80 08
[13177.824659] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[13177.835617] sd 6:0:0:0: [sdb] 65536 512-byte hardware sectors (34 MB)
[13177.853635] sd 6:0:0:0: [sdb] Write Protect is on
[13177.853647] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 80 08
[13177.853653] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[13177.853664]  sdb: unknown partition table
[13177.886022] sd 6:0:0:0: [sdb] Attached SCSI disk
[13177.886107] sd 6:0:0:0: Attached scsi generic sg2 type 0


There is a small partition on the drive that they save the windows software on.  So I unmount this then I did this.
I downloaded this: [http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-0.9.6.tar.bz2](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-0.9.6.tar.bz2)

From here:
[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

I then downloaded this:
[http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf)

I extracted the first file and copied the file "usb_modeswitch" to /usr/sbin.

I then created a file called "initmodem.sh" in the same dir with these contents:

> modprobe usbserial vendor=0x1c9e product=0x6061 && usb_modeswitch
sleep 3

I gave it execution rights.  I then copied this "usb_modeswitch.conf" to /etc, and I edit it.

I look for this line:

> #Alcatel OT-X020 (aka MBD-100HU, aka Nuton 3.5G), works with Emobile D11LC
# Contributor: Aleksandar Samardzic
;DefaultVendor= 0x1c9e
;DefaultProduct= 0x1001
;TargetVendor= 0x1c9e
;TargetProduct= 0x6061
;MessageEndpoint=0x05
;MessageContent="55534243123456780000000000000606f504025270000000000000000

And I change it to this:

> Alcatel OT-X020 (aka MBD-100HU, aka Nuton 3.5G), works with Emobile D11LC
# Contributor: Aleksandar Samardzic
DefaultVendor= 0x1c9e
DefaultProduct= 0x1001
TargetVendor= 0x1c9e
TargetProduct= 0x6061
MessageEndpoint=0x05
MessageContent="55534243123456780000000000000606f50402527000000000000000000000" 

I basically uncommented everything.

I save it then I open this file for editing "wvdial.conf".

I replace everything in the file with this:

> [Dialer Defaults]
Phone = *99#
Username = guest
Password = guest
Modem = /dev/ttyACM0
Stupid Mode = 1
Dial Command = ATDT
[Dialer smartbro]
Init1 = ATZ
Init2 = ATE1
Init3 = AT+CGDCONT=1,"IP","broadband.tigo.gt","",0,0
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
New PPPD = yes
Baud = 912600
Idle Seconds = 3000
Auto DNS = 1
Stupid Mode = 1
Compuserve = 0
Dial Command = ATD
Ask Password = 0
FlowControl = NOFLOW

I now connect my USB Modem, I unmount it then I run this:

sudo /usr/sbin/initmodem.sh

This is what I get in response:

>  * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 0.9.6 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices
 No target device found
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

This is what the tutorial says I should get:

> * usb_modeswitch: tool for controlling "flip flop" mode USB devices
* Version 0.9.6 (C) Josua Dietze 2009
* Works with libusb 0.1.12 and probably other versions
Looking for target devices
No target device found
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

So I see it executes correctly.  I then go back to console and run this:

sudo wvdial smartbro

I am supposed to get this:

> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATE1
ATE1
OK
--> Sending: AT+CGDCONT=1,"IP","broadband.tigo.gt","",0,0
AT+CGDCONT=1,"IP","broadband.tigo.gt","",0,0
OK
--> Modem initialized.
--> Idle Seconds = 3000, disabling automatic reconnect.
--> Sending: ATD*99#
--> Waiting for carrier.
ATD*99#
CONNECT
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sat Mar 21 07:55:06 2009
--> Pid of pppd: 6085
--> pppd: h[08]&#65533;[08]
--> Using interface ppp0
--> pppd: h[08]&#65533;[08]
--> pppd: h[08]&#65533;[08]
--> pppd: h[08]&#65533;[08]
--> pppd: h[08]&#65533;[08]
--> pppd: h[08]&#65533;[08]
--> pppd: h[08]&#65533;[08]
--> local IP address 10.248.135.239
--> pppd: h[08]&#65533;[08]
--> remote IP address 10.64.64.64
--> pppd: h[08]&#65533;[08]
--> primary DNS address 200.49.160.31
--> pppd: h[08]&#65533;[08]
--> secondary DNS address 200.49.160.35
--> pppd: h[08]&#65533;[08]

And it is supposed to connect, but this is what I get:

> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

This file ttyUSB0 does not exist.  libusb is installed and libusb-dev is installed.

This is what I get from lsusb and dmesg after running the first script, respectively.

> Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 013: ID 1c9e:6061
Bus 001 Device 003: ID 045e:0053 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000

> [13635.576216] usb 1-2: USB disconnect, address 12
[13637.465062] usb 1-2: new full speed USB device using ohci_hcd and address 13
[13637.996007] usb 1-2: configuration #1 chosen from 1 choice

Now I tried creating the ttyUSB0 file using mkmod:

sudo mknod /dev/ttyUSB0 c 188 0

And this is now what I get when I run the wvdial command:

> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such device
--> Cannot open /dev/ttyUSB0: No such device
--> Cannot open /dev/ttyUSB0: No such device

Ok what is going on here and how do I get ttyUSB0 to be created to the system when it switches device parameters from drive to modem?

I do have these files in my /dev dir that change when I insert the usb drive and change it to a modem:

> /dev/usbdev1.1_ep00
/dev/usbdev1.1_ep81
/dev/usbdev1.3_ep00
/dev/usbdev1.3_ep81
/dev/usbdev1.13_ep00
/dev/usbdev1.13_ep02
/dev/usbdev1.13_ep04
/dev/usbdev1.13_ep05
/dev/usbdev1.13_ep81
/dev/usbdev1.13_ep82
/dev/usbdev1.13_ep84
/dev/usbdev1.13_ep85
/dev/usbdev2.1_ep00
/dev/usbdev2.1_ep81
/dev/usbdev3.1_ep00
/dev/usbdev3.1_ep81

Any one got any ideas??

---

### Post by GeorgeVita on 2009-06-15
Hi **jfreak53**,

First check if your modem is attached as **Modem = /dev/ttyACM0**
or as **Modem = /dev/ttyUSB0** (you have 2 definitions within /etc/wvdial.conf). Parameters into this file are merged before used (see terminal command: **man wvdial** and **man wvdial.conf**). If you have only one modem, place all parameters to "defaults" section and dial using **sudo wvdial**

If above don't fix it try the following:

test: **ls /dev/ttyU* /dev/ttyA* /dev/ttyH*** to see any serial port
run your script: **sudo /usr/sbin/initmodem.sh**
try **lsusb** to confirm modem state (**1c9e : 6061**)
then try manually: **sudo modprobe usbserial vendor=0x1c9e product=0x6061**
test: **ls /dev/ttyU* /dev/ttyA* /dev/ttyH*** to see any new serial port
conclude with: **dmesg**

Finally check all above booting with/without the modem attached.

Hope to find a solution!
Regards,
George

---

### Post by jeffrapp on 2009-07-15
I  have the same modem, which I use in Guatemala. I simply plugged it in, let the drivers load. I do not try to connect with the "connect to a network" function on the computer (Windows Vista). It is necessary to open the application (which is called Interent Movil Tigo), which then initializes the modem. After initializasing, another box opens which allows you to connect to the internet. It works fine for me.
Incidentally, I would like to use it in Honduras, but I believe it is locked. Does anyone know how to unlock this modem?
Thanks

---

